# Viral evolution. Lab Notebook

We downloaded the sequenced reads from the link by the `wget` command. 
```
$ wget http://ftp.sra.ebi.ac.uk/vol1/fastq/SRR170/001/SRR1705851/SRR1705851.fastq.gz
```
Then we run fastqc for sequenced reads (look at SRR1705851_fastqc.html file).
```
$ fastqc -o . SRR1705851.fastq.gz 
```
We run the bwa-mem algorithm for alignment and process the results with the VarScan program. To find the global differences between roommate strain and reference, we set the frequency threshold equal to 0.95.
```
$ bwa index sequence.fasta
$ bwa mem sequence.fasta SRR1705851.fastq.gz | samtools view -S -b - | samtools sort - -o roommate.bam
$ samtools flagstat roommate.bam
$ samtools index roommate.bam 
$ samtools mpileup -f sequence.fasta roommate.bam -d 32011 >  my.mpileup
$ java -jar ~/VarScan.v2.4.4.jar  mpileup2snp my.mpileup --min-var-freq 0.95 --variants --output-vcf 1 > VarScan_results_95.vcf
$ cat VarScan_results_95.vcf | awk 'NR>24 {print $1, $2, $4, $5}' | wc -l
```
There were five mutations:

1. A72G -- synonymous

2. C117T -- synonymous

3. T774C -- synonymous

4. C999T -- synonymous

5. A1260C -- synonymous

Then we wanted to find the mutated viral particles by setting the frequency threshold equal to 0.001.
```
$ java -jar ~/VarScan.v2.4.4.jar  mpileup2snp my.mpileup --min-var-freq 0.001 --variants --output-vcf 1 > VarScan_results_0_1.vcf
```
There were thirteen new mutations:

1. A254G (0.19%) -- missense D73G

2. C307T (0.95%) -- missense P91S

3. T340C (0.18%) -- missense S101P

4. T389C (0.23%) -- missense V118A

5. A722G (0.23%) -- missense D229G

6. A744G (0.18%) -- synonymous

7. A802G (0.24%) -- missense M256V

8. T915C (0.2%) -- synonymous

9. A1043G (0.19%) -- missense D336G

10. A1086G (0.21%) -- synonymous 

11. A1213G (0.22%) -- missense R393G

12. T1280C (0.18%) -- missense L415P

13. T1458C (0.83%) -- synonymous

Among these mutations, there are errors from the sequencer. That's why sequencing of a homogenous viral population was done three times. We repeated the procedure with these three controls.
```
$ cat VarScan_results_0_1.vcf | awk 'NR>24 {print $1, $2, $4, $5}' | wc -l
$ wget ftp://ftp.sra.ebi.ac.uk/vol1/fastq/SRR170/008/SRR1705858/SRR1705858.fastq.gz
$ wget ftp://ftp.sra.ebi.ac.uk/vol1/fastq/SRR170/009/SRR1705859/SRR1705859.fastq.gz
$ wget ftp://ftp.sra.ebi.ac.uk/vol1/fastq/SRR170/000/SRR1705860/SRR1705860.fastq.gz
$ fastqc -o . SRR1705858.fastq.gz SRR1705859.fastq.gz SRR1705860.fastq.gz 
$ bwa mem sequence.fasta SRR1705858.fastq.gz | samtools view -S -b - | samtools sort - -o control_1.bam
$ bwa mem sequence.fasta SRR1705859.fastq.gz | samtools view -S -b - | samtools sort - -o control_2.bam
$ bwa mem sequence.fasta SRR1705860.fastq.gz | samtools view -S -b - | samtools sort - -o control_3.bam
$ samtools flagstat control_1.bam
$ samtools flagstat control_2.bam
$ samtools flagstat control_3.bam
$ samtools index control_1.bam
$ samtools index control_2.bam
$ samtools index control_3.bam
$ samtools mpileup -f sequence.fasta control_1.bam -d 22926 >  control_1.mpileup
$ samtools mpileup -f sequence.fasta control_2.bam -d 20848 >  control_2.mpileup
$ samtools mpileup -f sequence.fasta control_3.bam -d 22335 >  control_3.mpileup
$ java -jar ~/VarScan.v2.4.4.jar  mpileup2snp control_1.mpileup --min-var-freq 0.001 --variants --output-vcf 1 > VarScan_control_1_results_0_1.vcf
$ java -jar ~/VarScan.v2.4.4.jar  mpileup2snp control_2.mpileup --min-var-freq 0.001 --variants --output-vcf 1 > VarScan_control_2_results_0_1.vcf
$ java -jar ~/VarScan.v2.4.4.jar  mpileup2snp control_3.mpileup --min-var-freq 0.001 --variants --output-vcf 1 > VarScan_control_3_results_0_1.vcf
```
Then we filter the mutations by the VarScanParser script. You can find the html file with the results. Overall, there were two significant mutations:

1. C307T (0.95%) -- missense P91S => mutation in epitope E

2. T1458C (0.83%) -- synonymous
