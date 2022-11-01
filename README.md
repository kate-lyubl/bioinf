# Viral evolution

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
