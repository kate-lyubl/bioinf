# Viral evolution. Lab Notebook

```
$ wget http://ftp.sra.ebi.ac.uk/vol1/fastq/SRR170/001/SRR1705851/SRR1705851.fastq.gz
$ fastqc -o . SRR1705851.fastq.gz 
$ bwa index sequence.fasta
$ bwa mem sequence.fasta SRR1705851.fastq.gz | samtools view -S -b - | samtools sort - -o roommate.bam
$ samtools flagstat roommate.bam
$ samtools index roommate.bam 
$ samtools mpileup -f sequence.fasta roommate.bam -d 32011 >  my.mpileup
$ java -jar ~/VarScan.v2.4.4.jar  mpileup2snp my.mpileup --min-var-freq 0.95 --variants --output-vcf 1 > VarScan_results_95.vcf
$ cat VarScan_results_95.vcf | awk 'NR>24 {print $1, $2, $4, $5}' | wc -l
```
A72G -- synonymous

C117T -- synonymous

T774C -- synonymous

C999T -- synonymous

A1260C -- synonymous

```
$ java -jar ~/VarScan.v2.4.4.jar  mpileup2snp my.mpileup --min-var-freq 0.001 --variants --output-vcf 1 > VarScan_results_0_1.vcf
```
A254G (0.19%) -- missense D73G

C307T (0.95%) -- missense P91S

T340C (0.18%) -- missense S101P

T389C (0.23%) -- missense V118A

A722G (0.23%) -- missense D229G

A744G (0.18%) -- synonymous

A802G (0.24%) -- missense M256V

T915C (0.2%) -- synonymous

A1043G (0.19%) -- missense D336G

A1086G (0.21%) -- synonymous 

A1213G (0.22%) -- missense R393G

T1280C (0.18%) -- missense L415P

T1458C (0.83%) -- synonymous

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

C307T (0.95%) -- missense P91S => epitope E

T1458C (0.83%) -- synonymous
