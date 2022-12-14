# Tardigrades: from genestealers to space marines. Lab notebook

## Obtaining data. Genome sequence.

Dowload assembled genome
```
wget http://ftp.ncbi.nlm.nih.gov/genomes/all/GCA/001/949/185/GCA_001949185.1_Rvar_4.0/GCA_001949185.1_Rvar_4.0_genomic.fna.gz
```
## Structural annotation.

Then we downloaded AUGUSTUS results from https://drive.google.com/file/d/1wBxf6cDgu22NbjAOgTe-8b3Zx60hNKY0/view?usp=drive_web and getAnnoFasta.pl script
```
wget http://augustus.gobics.de/binaries/scripts/getAnnoFasta.pl
```
Protein sequences were extracted by this script and put in augustus.whole.aa
```
perl getAnnoFasta.pl augustus.whole.gff 
```
We counted the number of obtained proteins by the command below and recieved 16435 proteins.
```
cat augustus.whole.aa | grep \> | wc -l
```
## Physical localization

Then we obtained a list of peptides that were associated with the DNA from https://disk.yandex.ru/d/xJqQMGX77Xueqg. With `blast` we created data base and searched which proteins from the _R. varieornatus_ genome correspond to peptides.fa.
```
makeblastdb -in augustus.whole.aa -dbtype prot  -out trad_db
blastp -db trad_db -query peptides.fa -outfmt 6  -out searched_prot
```
For determination of protein of interests, we made a list of proteins and then with `samtools faidx` selected ones. As a result, we decreased the number of proteins from 16435 to 34.
```
cat searched_prot | cut -f 2 | sort -u > protein_names.txt
xargs samtools faidx augustus.whole.aa < protein_names.txt > poi.aa
```
## Localization prediction.

To predict the subcellular localization of proteins, we used WoLF PSORT server. The results could be seen in file wolf_results.html.

## BLAST search

We BLASTed protein sequences against the “UniProtKB/Swiss-Prot” database and recieved the next results.

| protein ID | Accession Number | Description                   | Organism             | Score | Identities (%) | E-value  |
|------------|------------------|-------------------------------|----------------------|-------|----------------|----------|
| g10513.t1  | A8PUH4           | Fibroin heavy chain-like      | Malassezia globosa   | 157   | 37.9           | 5.5e-42  |
| g10514.t1  | A0A094BV12       | Stress protein DDR48          | Pseudogymnoascus     | 72    | 25.3           | 1.8e-11  |
| g11806.t1  | A8PUH4           | Fibroin heavy chain-like      | Malassezia globosa   | 101   | 47.4           | 3.3e-22  |
| g11960.t1  | A0A4C1TJ24       | E3 ubiquitin protein ligase   | Eumeta variegata     | 477   | 32.9           | 4.6e-150 |
| g14472.t1  | A0A8C4AFV5       | SEA domain-containing protein | Denticeps clupeoides | 144   | 24.4           | 2.9e-33  |
| g15484.t1  | K1PPB4           | Vacuolar protein sorting-associated protein 51 homolog | Crassostrea gigas | 701 | 50.9 | 0 |
| g16318.t1  | A0A0A2L576       | Stress protein DDR48          | Penicillium italicum | 148   | 36.4           | 1.7e-38  |
| g16368.t1  | A0A0A2L576       | Stress protein DDR48          | Penicillium italicum | 134   | 34.8           | 1.5e-33  |
| g5927.t1   | R7UWI1           | Glucosamine 6-phosphate N-acetyltransferase | Capitella teleta | 112 | 43.8 | 9.8e-25    |
| g7861.t1   | A0A6L2PMM2       | SWI/SNF-related matrix-associated actin-dependent regulator of chromatin subfamily A-like protein 1 | Coptotermes formosanus | 299 | 38.5 | 1.2e-88 |
| g8100.t1   | A0A7F5RFC7       | putative inositol monophosphatase 3 | Agrilus planipennis | 204 | 37.9        | 1.6e-54  |
| g8312.t1   | A0A8J1UKA6       | Vacuolar protein sorting-associated protein 41 homolog | Owenia fusiformis | 637 | 42.6 | 0 |

## Pfam prediction

We predicted the function of the proteins using HMMER (web-version, https://www.ebi.ac.uk/Tools/hmmer/).

| Query Name | Top Hit Identifier | Description |
|------------|--------------------|-------------|
| g10513.t1  |         -          |      -      |
| g10514.t1  |         -          |      -      |
| g11806.t1  |         -          |      -      |
| g11960.t1  |      zf-C3HC4      | Zinc finger, C3HC4 type (RING finger) |
| g14472.t1  |         -          |      -      |
| g15484.t1  |        Vps51       | Vps51/Vps67 |
| g16318.t1  |         -          |      -      |
| g16368.t1  |         -          |      -      |
| g5927.t1   |         -          |      -      |
| g7861.t1   |     SNF2-rel_dom   | SNF2-related domain |
| g8100.t1   |     Inositol_P     | Inositol monophosphatase family |
| g8312.t1   |      Clathrin      | Region in Clathrin and VPS |
 
## Integration of various pieces of evidence

| Query Name | Blast Best Hit's Annotation | Blast Best Hit's e-value | Predicted Pfam domain | Localization According to WoLF | localization according to TargetP |
|------------|-----------------------------|--------------------------|-----------------------|--------------------------------|-----------------------------------|
| g10513.t1  | Fibroin heavy chain-like | 5.5e-42 | - | Nuclear | Other |
| g10514.t1  | Stress protein DDR48 | 1.8e-11 | - | Nuclear | Other |
| g11806.t1  | Fibroin heavy chain-like | 3.3e-22 | - | Nuclear | Other |
| g11960.t1  | E3 ubiquitin protein ligase | 4.6e-150 | Zinc finger, C3HC4 type (RING finger) | Nuclear | Other |
| g14472.t1  | SEA domain-containing protein | 2.9e-33 | - | Nuclear | Other |
| g15484.t1  | Vacuolar protein sorting-associated protein 51 homolog | 0 | Vps51/Vps67 | Nuclear | Other |
| g16318.t1  | Stress protein DDR48 | 1.7e-38 | - | Nuclear | Other |
| g16368.t1  | Stress protein DDR48 | 1.5e-33 | - | Nuclear | Other |
| g5927.t1   | Glucosamine 6-phosphate N-acetyltransferase | 9.8e-25 | - | Nuclear | Other |
| g7861.t1   | SWI/SNF-related matrix-associated actin-dependent regulator of chromatin subfamily A-like protein 1 | 1.2e-88 | SNF2-related domain | Nuclear | Other |
| g8100.t1   | putative inositol monophosphatase 3 | 1.6e-54 | Inositol monophosphatase family | Nuclear | Other |
| g8312.t1   | Vacuolar protein sorting-associated protein 41 homolog | 0 | Region in Clathrin and VPS | Nuclear | Other |
