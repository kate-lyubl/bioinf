# Lab Journal. RNA-seq

## Input data

```
$ wget http://ftp.sra.ebi.ac.uk/vol1/fastq/SRR941/SRR941816/SRR941816.fastq.gz http://ftp.sra.ebi.ac.uk/vol1/fastq/SRR941/SRR941817/SRR941817.fastq.gz http://ftp.sra.ebi.ac.uk/vol1/fastq/SRR941/SRR941818/SRR941818.fastq.gz http://ftp.sra.ebi.ac.uk/vol1/fastq/SRR941/SRR941819/SRR941819.fastq.gz

--2023-03-01 17:44:00--  http://ftp.sra.ebi.ac.uk/vol1/fastq/SRR941/SRR941816/SRR941816.fastq.gz
Resolving ftp.sra.ebi.ac.uk (ftp.sra.ebi.ac.uk)... 193.62.193.138
Connecting to ftp.sra.ebi.ac.uk (ftp.sra.ebi.ac.uk)|193.62.193.138|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 433539958 (413M) [application/x-gzip]
Saving to: ‘SRR941816.fastq.gz’

SRR941816.fastq.gz                                    24%[===========================>                                                                                        ] 102,69M  1,16MB/s    eta 4mSRR941816.fastq.gz                                 100%[===============================================================================================================>] 413,46M  1,20MB/s    in 7m 21s  

2023-03-01 17:51:21 (960 KB/s) - ‘SRR941816.fastq.gz’ saved [433539958/433539958]

--2023-03-01 17:51:21--  http://ftp.sra.ebi.ac.uk/vol1/fastq/SRR941/SRR941817/SRR941817.fastq.gz
Reusing existing connection to ftp.sra.ebi.ac.uk:80.
HTTP request sent, awaiting response... 200 OK
Length: 477099436 (455M) [application/x-gzip]
Saving to: ‘SRR941817.fastq.gz’

SRR941817.fastq.gz                                    18%[====================>                                                                                                 ]  84,10M  1,25MB/s    eta SRR94181SRR941817.fastq.gz                                    98%[==================================================================================================================>   ] 446,74M   982KB/sSRR941817.fastq.gz                                 100%[===============================================================================================================>] 455,00M   824KB/s    in 6m 39s  

2023-03-01 17:58:01 (1,14 MB/s) - ‘SRR941817.fastq.gz’ saved [477099436/477099436]

--2023-03-01 17:58:01--  http://ftp.sra.ebi.ac.uk/vol1/fastq/SRR941/SRR941818/SRR941818.fastq.gz
Reusing existing connection to ftp.sra.ebi.ac.uk:80.
HTTP request sent, awaiting response... 200 OK
Length: 83133773 (79M) [application/x-gzip]
Saving to: ‘SRR941818.fastq.gz’

SRR941818.fastq.gz                                 100%[===============================================================================================================>]  79,28M  1,18MB/s    in 70s     

2023-03-01 17:59:11 (1,13 MB/s) - ‘SRR941818.fastq.gz’ saved [83133773/83133773]

--2023-03-01 17:59:11--  http://ftp.sra.ebi.ac.uk/vol1/fastq/SRR941/SRR941819/SRR941819.fastq.gz
Reusing existing connection to ftp.sra.ebi.ac.uk:80.
HTTP request sent, awaiting response... 200 OK
Length: 295598163 (282M) [application/x-gzip]
Saving to: ‘SRR941819.fastq.gz’

SRR941819.fastq.gz                                 100%[===============================================================================================================>] 281,90M  1,22MB/s    in 4m 48s  

2023-03-01 18:04:00 (1003 KB/s) - ‘SRR941819.fastq.gz’ saved [295598163/295598163]

FINISHED --2023-03-01 18:04:00--
Total wall clock time: 20m 0s
Downloaded: 4 files, 1,2G in 19m 58s (1,03 MB/s)
```

```
$ wget http://ftp.ncbi.nlm.nih.gov/genomes/all/GCF/000/146/045/GCF_000146045.2_R64/GCF_000146045.2_R64_genomic.fna.gz http://ftp.ncbi.nlm.nih.gov/genomes/all/GCF/000/146/045/GCF_000146045.2_R64/GCF_000146045.2_R64_genomic.gff.gz

--2023-03-01 18:05:23--  http://ftp.ncbi.nlm.nih.gov/genomes/all/GCF/000/146/045/GCF_000146045.2_R64/GCF_000146045.2_R64_genomic.fna.gz
Resolving ftp.ncbi.nlm.nih.gov (ftp.ncbi.nlm.nih.gov)... 130.14.250.12, 130.14.250.13, 2607:f220:41f:250::228, ...
Connecting to ftp.ncbi.nlm.nih.gov (ftp.ncbi.nlm.nih.gov)|130.14.250.12|:80... connected.
HTTP request sent, awaiting response... 301 Moved Permanently
Location: https://ftp.ncbi.nlm.nih.gov/genomes/all/GCF/000/146/045/GCF_000146045.2_R64/GCF_000146045.2_R64_genomic.fna.gz [following]
--2023-03-01 18:05:24--  https://ftp.ncbi.nlm.nih.gov/genomes/all/GCF/000/146/045/GCF_000146045.2_R64/GCF_000146045.2_R64_genomic.fna.gz
Connecting to ftp.ncbi.nlm.nih.gov (ftp.ncbi.nlm.nih.gov)|130.14.250.12|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 3843460 (3,7M) [application/x-gzip]
Saving to: ‘GCF_000146045.2_R64_genomic.fna.gz’

GCF_000146045.2_R64_genomic.fna.gz                 100%[===============================================================================================================>]   3,67M  1,51MB/s    in 2,4s    

2023-03-01 18:05:27 (1,51 MB/s) - ‘GCF_000146045.2_R64_genomic.fna.gz’ saved [3843460/3843460]

URL transformed to HTTPS due to an HSTS policy
--2023-03-01 18:05:27--  https://ftp.ncbi.nlm.nih.gov/genomes/all/GCF/000/146/045/GCF_000146045.2_R64/GCF_000146045.2_R64_genomic.gff.gz
Reusing existing connection to ftp.ncbi.nlm.nih.gov:443.
HTTP request sent, awaiting response... 200 OK
Length: 2183228 (2,1M) [application/x-gzip]
Saving to: ‘GCF_000146045.2_R64_genomic.gff.gz’

GCF_000146045.2_R64_genomic.gff.gz                 100%[===============================================================================================================>]   2,08M  1,59MB/s    in 1,3s    

2023-03-01 18:05:28 (1,59 MB/s) - ‘GCF_000146045.2_R64_genomic.gff.gz’ saved [2183228/2183228]

FINISHED --2023-03-01 18:05:28--
Total wall clock time: 5,3s
Downloaded: 2 files, 5,7M in 3,7s (1,54 MB/s)
```

## Analysis Pipeline
### Aligning with HISAT2
```
$ gunzip GCF_000146045.2_R64_genomic.fna.gz
$ hisat2-build GCF_000146045.2_R64_genomic.fna genome

Settings:
  Output files: "genome.*.ht2"
  Line rate: 6 (line is 64 bytes)
  Lines per side: 1 (side is 64 bytes)
  Offset rate: 4 (one in 16)
  FTable chars: 10
  Strings: unpacked
  Local offset rate: 3 (one in 8)
  Local fTable chars: 6
  Local sequence length: 57344
  Local sequence overlap between two consecutive indexes: 1024
  Endianness: little
  Actual local endianness: little
  Sanity checking: disabled
  Assertions: disabled
  Random seed: 0
  Sizeofs: void*:8, int:4, long:8, size_t:8
Input files DNA, FASTA:
  GCF_000146045.2_R64_genomic.fna
Reading reference sizes
  Time reading reference sizes: 00:00:00
Calculating joined length
Writing header
Reserving space for joined string
Joining reference sequences
  Time to join reference sequences: 00:00:00
  Time to read SNPs and splice sites: 00:00:00
Using parameters --bmax 2279457 --dcv 1024
  Doing ahead-of-time memory usage test
  Passed!  Constructing with these parameters: --bmax 2279457 --dcv 1024
Constructing suffix-array element generator
Building DifferenceCoverSample
  Building sPrime
  Building sPrimeOrder
  V-Sorting samples
  V-Sorting samples time: 00:00:00
  Allocating rank array
  Ranking v-sort output
  Ranking v-sort output time: 00:00:00
  Invoking Larsson-Sadakane on ranks
  Invoking Larsson-Sadakane on ranks time: 00:00:00
  Sanity-checking and returning
Building samples
Reserving space for 12 sample suffixes
Generating random suffixes
QSorting 12 sample offsets, eliminating duplicates
QSorting sample offsets, eliminating duplicates time: 00:00:00
Multikey QSorting 12 samples
  (Using difference cover)
  Multikey QSorting samples time: 00:00:00
Calculating bucket sizes
Splitting and merging
  Splitting and merging time: 00:00:00
Avg bucket size: 1.73673e+06 (target: 2279456)
Converting suffix-array elements to index image
Allocating ftab, absorbFtab
Entering GFM loop
Getting block 1 of 7
  Reserving size (2279457) for bucket 1
  Calculating Z arrays for bucket 1
  Entering block accumulator loop for bucket 1:
  bucket 1: 10%
  bucket 1: 20%
  bucket 1: 30%
  bucket 1: 40%
  bucket 1: 50%
  bucket 1: 60%
  bucket 1: 70%
  bucket 1: 80%
  bucket 1: 90%
  bucket 1: 100%
  Sorting block of length 1917483 for bucket 1
  (Using difference cover)
  Sorting block time: 00:00:00
Returning block of 1917484 for bucket 1
Getting block 2 of 7
  Reserving size (2279457) for bucket 2
  Calculating Z arrays for bucket 2
  Entering block accumulator loop for bucket 2:
  bucket 2: 10%
  bucket 2: 20%
  bucket 2: 30%
  bucket 2: 40%
  bucket 2: 50%
  bucket 2: 60%
  bucket 2: 70%
  bucket 2: 80%
  bucket 2: 90%
  bucket 2: 100%
  Sorting block of length 1565107 for bucket 2
  (Using difference cover)
  Sorting block time: 00:00:00
Returning block of 1565108 for bucket 2
Getting block 3 of 7
  Reserving size (2279457) for bucket 3
  Calculating Z arrays for bucket 3
  Entering block accumulator loop for bucket 3:
  bucket 3: 10%
  bucket 3: 20%
  bucket 3: 30%
  bucket 3: 40%
  bucket 3: 50%
  bucket 3: 60%
  bucket 3: 70%
  bucket 3: 80%
  bucket 3: 90%
  bucket 3: 100%
  Sorting block of length 2077071 for bucket 3
  (Using difference cover)
  Sorting block time: 00:00:00
Returning block of 2077072 for bucket 3
Getting block 4 of 7
  Reserving size (2279457) for bucket 4
  Calculating Z arrays for bucket 4
  Entering block accumulator loop for bucket 4:
  bucket 4: 10%
  bucket 4: 20%
  bucket 4: 30%
  bucket 4: 40%
  bucket 4: 50%
  bucket 4: 60%
  bucket 4: 70%
  bucket 4: 80%
  bucket 4: 90%
  bucket 4: 100%
  Sorting block of length 1959963 for bucket 4
  (Using difference cover)
  Sorting block time: 00:00:00
Returning block of 1959964 for bucket 4
Getting block 5 of 7
  Reserving size (2279457) for bucket 5
  Calculating Z arrays for bucket 5
  Entering block accumulator loop for bucket 5:
  bucket 5: 10%
  bucket 5: 20%
  bucket 5: 30%
  bucket 5: 40%
  bucket 5: 50%
  bucket 5: 60%
  bucket 5: 70%
  bucket 5: 80%
  bucket 5: 90%
  bucket 5: 100%
  Sorting block of length 1858740 for bucket 5
  (Using difference cover)
  Sorting block time: 00:00:00
Returning block of 1858741 for bucket 5
Getting block 6 of 7
  Reserving size (2279457) for bucket 6
  Calculating Z arrays for bucket 6
  Entering block accumulator loop for bucket 6:
  bucket 6: 10%
  bucket 6: 20%
  bucket 6: 30%
  bucket 6: 40%
  bucket 6: 50%
  bucket 6: 60%
  bucket 6: 70%
  bucket 6: 80%
  bucket 6: 90%
  bucket 6: 100%
  Sorting block of length 630502 for bucket 6
  (Using difference cover)
  Sorting block time: 00:00:00
Returning block of 630503 for bucket 6
Getting block 7 of 7
  Reserving size (2279457) for bucket 7
  Calculating Z arrays for bucket 7
  Entering block accumulator loop for bucket 7:
  bucket 7: 10%
  bucket 7: 20%
  bucket 7: 30%
  bucket 7: 40%
  bucket 7: 50%
  bucket 7: 60%
  bucket 7: 70%
  bucket 7: 80%
  bucket 7: 90%
  bucket 7: 100%
  Sorting block of length 2148233 for bucket 7
  (Using difference cover)
  Sorting block time: 00:00:01
Returning block of 2148234 for bucket 7
Exited GFM loop
fchr[A]: 0
fchr[C]: 3766349
fchr[G]: 6086925
fchr[T]: 8404025
fchr[$]: 12157105
Exiting GFM::buildToDisk()
Returning from initFromVector
Wrote 8248454 bytes to primary GFM file: genome.1.ht2
Wrote 3039284 bytes to secondary GFM file: genome.2.ht2
Re-opening _in1 and _in2 as input streams
Returning from GFM constructor
Returning from initFromVector
Wrote 5399069 bytes to primary GFM file: genome.5.ht2
Wrote 3092708 bytes to secondary GFM file: genome.6.ht2
Re-opening _in5 and _in5 as input streams
Returning from HGFM constructor
Headers:
    len: 12157105
    gbwtLen: 12157106
    nodes: 12157106
    sz: 3039277
    gbwtSz: 3039277
    lineRate: 6
    offRate: 4
    offMask: 0xfffffff0
    ftabChars: 10
    eftabLen: 0
    eftabSz: 0
    ftabLen: 1048577
    ftabSz: 4194308
    offsLen: 759820
    offsSz: 3039280
    lineSz: 64
    sideSz: 64
    sideGbwtSz: 48
    sideGbwtLen: 192
    numSides: 63319
    numLines: 63319
    gbwtTotLen: 4052416
    gbwtTotSz: 4052416
    reverse: 0
    linearFM: Yes
Total time for call to driver() for forward index: 00:00:04
```

```
$ gunzip SRR94181*
$ fastqc SRR94181*

Started analysis of SRR941816.fastq
Approx 5% complete for SRR941816.fastq
Approx 10% complete for SRR941816.fastq
Approx 15% complete for SRR941816.fastq
Approx 20% complete for SRR941816.fastq
Approx 25% complete for SRR941816.fastq
Approx 30% complete for SRR941816.fastq
Approx 35% complete for SRR941816.fastq
Approx 40% complete for SRR941816.fastq
Approx 45% complete for SRR941816.fastq
Approx 50% complete for SRR941816.fastq
Approx 55% complete for SRR941816.fastq
Approx 60% complete for SRR941816.fastq
Approx 65% complete for SRR941816.fastq
Approx 70% complete for SRR941816.fastq
Approx 75% complete for SRR941816.fastq
Approx 80% complete for SRR941816.fastq
Approx 85% complete for SRR941816.fastq
Approx 90% complete for SRR941816.fastq
Approx 95% complete for SRR941816.fastq
Analysis complete for SRR941816.fastq
Started analysis of SRR941817.fastq
Approx 5% complete for SRR941817.fastq
Approx 10% complete for SRR941817.fastq
Approx 15% complete for SRR941817.fastq
Approx 20% complete for SRR941817.fastq
Approx 25% complete for SRR941817.fastq
Approx 30% complete for SRR941817.fastq
Approx 35% complete for SRR941817.fastq
Approx 40% complete for SRR941817.fastq
Approx 45% complete for SRR941817.fastq
Approx 50% complete for SRR941817.fastq
Approx 55% complete for SRR941817.fastq
Approx 60% complete for SRR941817.fastq
Approx 65% complete for SRR941817.fastq
Approx 70% complete for SRR941817.fastq
Approx 75% complete for SRR941817.fastq
Approx 80% complete for SRR941817.fastq
Approx 85% complete for SRR941817.fastq
Approx 90% complete for SRR941817.fastq
Approx 95% complete for SRR941817.fastq
Analysis complete for SRR941817.fastq
Started analysis of SRR941818.fastq
Approx 5% complete for SRR941818.fastq
Approx 10% complete for SRR941818.fastq
Approx 15% complete for SRR941818.fastq
Approx 20% complete for SRR941818.fastq
Approx 25% complete for SRR941818.fastq
Approx 30% complete for SRR941818.fastq
Approx 35% complete for SRR941818.fastq
Approx 40% complete for SRR941818.fastq
Approx 45% complete for SRR941818.fastq
Approx 50% complete for SRR941818.fastq
Approx 55% complete for SRR941818.fastq
Approx 60% complete for SRR941818.fastq
Approx 65% complete for SRR941818.fastq
Approx 70% complete for SRR941818.fastq
Approx 75% complete for SRR941818.fastq
Approx 80% complete for SRR941818.fastq
Approx 85% complete for SRR941818.fastq
Approx 90% complete for SRR941818.fastq
Approx 95% complete for SRR941818.fastq
Analysis complete for SRR941818.fastq
Started analysis of SRR941819.fastq
Approx 5% complete for SRR941819.fastq
Approx 10% complete for SRR941819.fastq
Approx 15% complete for SRR941819.fastq
Approx 20% complete for SRR941819.fastq
Approx 25% complete for SRR941819.fastq
Approx 30% complete for SRR941819.fastq
Approx 35% complete for SRR941819.fastq
Approx 40% complete for SRR941819.fastq
Approx 45% complete for SRR941819.fastq
Approx 50% complete for SRR941819.fastq
Approx 55% complete for SRR941819.fastq
Approx 60% complete for SRR941819.fastq
Approx 65% complete for SRR941819.fastq
Approx 70% complete for SRR941819.fastq
Approx 75% complete for SRR941819.fastq
Approx 80% complete for SRR941819.fastq
Approx 85% complete for SRR941819.fastq
Approx 90% complete for SRR941819.fastq
Approx 95% complete for SRR941819.fastq
Analysis complete for SRR941819.fastq
```
Results of the fastqc analysis are in the fastqc_results folder.

```
$ hisat2 -p 10 -x genome -U SRR941816.fastq | samtools sort > out_1.bam

9043877 reads; of these:
  9043877 (100.00%) were unpaired; of these:
    512972 (5.67%) aligned 0 times
    7930587 (87.69%) aligned exactly 1 time
    600318 (6.64%) aligned >1 times
94.33% overall alignment rate
[bam_sort_core] merging from 2 files and 1 in-memory blocks...
```
```
$ hisat2 -p 10 -x genome -U SRR941817.fastq | samtools sort > out_2.bam

9929568 reads; of these:
  9929568 (100.00%) were unpaired; of these:
    505208 (5.09%) aligned 0 times
    8645381 (87.07%) aligned exactly 1 time
    778979 (7.85%) aligned >1 times
94.91% overall alignment rate
[bam_sort_core] merging from 2 files and 1 in-memory blocks...
```

```
$ hisat2 -p 10 -x genome -U SRR941818.fastq | samtools sort > out_3.bam

1721675 reads; of these:
  1721675 (100.00%) were unpaired; of these:
    65077 (3.78%) aligned 0 times
    1508002 (87.59%) aligned exactly 1 time
    148596 (8.63%) aligned >1 times
96.22% overall alignment rate
```

```
$ hisat2 -p 10 -x genome -U SRR941819.fastq | samtools sort > out_4.bam

6172452 reads; of these:
  6172452 (100.00%) were unpaired; of these:
    229688 (3.72%) aligned 0 times
    5368127 (86.97%) aligned exactly 1 time
    574637 (9.31%) aligned >1 times
96.28% overall alignment rate
[bam_sort_core] merging from 1 files and 1 in-memory blocks...
```

### Quantifying with featureCounts
```
$ gunzip GCF_000146045.2_R64_genomic.gff.gz 
$ gffread GCF_000146045.2_R64_genomic.gff -T -o annotation.gtf
$ featureCounts -g gene_id -a annotation.gtf -o feature_counts.txt out_*


        ==========     _____ _    _ ____  _____  ______          _____  
        =====         / ____| |  | |  _ \|  __ \|  ____|   /\   |  __ \ 
          =====      | (___ | |  | | |_) | |__) | |__     /  \  | |  | |
            ====      \___ \| |  | |  _ <|  _  /|  __|   / /\ \ | |  | |
              ====    ____) | |__| | |_) | | \ \| |____ / ____ \| |__| |
        ==========   |_____/ \____/|____/|_|  \_\______/_/    \_\_____/
	  v2.0.3

//========================== featureCounts setting ===========================\\
||                                                                            ||
||             Input files : 4 BAM files                                      ||
||                                                                            ||
||                           out_1.bam                                        ||
||                           out_2.bam                                        ||
||                           out_3.bam                                        ||
||                           out_4.bam                                        ||
||                                                                            ||
||             Output file : feature_counts.txt                               ||
||                 Summary : feature_counts.txt.summary                       ||
||              Paired-end : no                                               ||
||        Count read pairs : no                                               ||
||              Annotation : annotation.gtf (GTF)                             ||
||      Dir for temp files : ./                                               ||
||                                                                            ||
||                 Threads : 1                                                ||
||                   Level : meta-feature level                               ||
||      Multimapping reads : not counted                                      ||
|| Multi-overlapping reads : not counted                                      ||
||   Min overlapping bases : 1                                                ||
||                                                                            ||
\\============================================================================//

//================================= Running ==================================\\
||                                                                            ||
|| Load annotation file annotation.gtf ...                                    ||
||    Features : 6831                                                         ||
||    Meta-features : 6459                                                    ||
||    Chromosomes/contigs : 17                                                ||
||                                                                            ||
|| Process BAM file out_1.bam...                                              ||
||    Single-end reads are included.                                          ||
||    Total alignments : 9773843                                              ||
||    Successfully assigned alignments : 7283571 (74.5%)                      ||
||    Running time : 0.08 minutes                                             ||
||                                                                            ||
|| Process BAM file out_2.bam...                                              ||
||    Single-end reads are included.                                          ||
||    Total alignments : 10832704                                             ||
||    Successfully assigned alignments : 7983159 (73.7%)                      ||
||    Running time : 0.08 minutes                                             ||
||                                                                            ||
|| Process BAM file out_3.bam...                                              ||
||    Single-end reads are included.                                          ||
||    Total alignments : 1885543                                              ||
||    Successfully assigned alignments : 1401108 (74.3%)                      ||
||    Running time : 0.02 minutes                                             ||
||                                                                            ||
|| Process BAM file out_4.bam...                                              ||
||    Single-end reads are included.                                          ||
||    Total alignments : 6800273                                              ||
||    Successfully assigned alignments : 4972354 (73.1%)                      ||
||    Running time : 0.05 minutes                                             ||
||                                                                            ||
|| Write the final count table.                                               ||
|| Write the read assignment summary.                                         ||
||                                                                            ||
|| Summary of counting results can be found in file "feature_counts.txt.summ  ||
|| ary"                                                                       ||
||                                                                            ||
\\============================================================================//
```

```
$ cat feature_counts.txt | cut -f 1,7-10 > simple_counts.txt
```

### Find differentially expressed genes with Deseq2
