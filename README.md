# Human genome analysis. Lab journal

## Download the 23andMe data and unzip file

```
$ unzip SNP_raw_v4_Full_20170514175358.txt.zip 
```
## File conversion 

```
$ plink --23file SNP_raw_v4_Full_20170514175358.txt --recode vcf --out snps_clean --output-chr MT --snps-only just-acgt

PLINK v1.90b7 64-bit (16 Jan 2023)             www.cog-genomics.org/plink/1.9/
(C) 2005-2023 Shaun Purcell, Christopher Chang   GNU General Public License v3
Logging to snps_clean.log.
Options in effect:
  --23file SNP_raw_v4_Full_20170514175358.txt
  --out snps_clean
  --output-chr MT
  --recode vcf
  --snps-only just-acgt

15346 MB RAM detected; reserving 7673 MB for main workspace.
--23file: snps_clean-temporary.bed + snps_clean-temporary.bim +
snps_clean-temporary.fam written.
15125 variants with indel calls present.  '--snps-only no-DI' or
--list-23-indels may be useful here.
Inferred sex: male.
595401 out of 610526 variants loaded from .bim file.
1 person (1 male, 0 females) loaded from .fam.
Using 1 thread (no multithreaded calculations invoked).
Before main variant filters, 1 founder and 0 nonfounders present.
Calculating allele frequencies... done.
Warning: 103 het. haploid genotypes present (see snps_clean.hh ); many commands
treat these as missing.
Total genotyping rate is 0.989246.
595401 variants and 1 person pass filters and QC.
Note: No phenotypes present.
--recode vcf to snps_clean.vcf ... done.
```

## Origins, haplogroups

Best mtDNA Haplogroup Matches:

1) H(T152C)

Defining Markers for haplogroup H(T152C):
HVR2: 152C 263G
CR: 750G 1438G 4769G 8860G 15326G
HVR1:

Marker path from rCRS to haplogroup H(T152C):
H2a2a1(rCRS) ⇨ 263G ⇨ H2a2a ⇨ 8860G 15326G ⇨ H2a2 ⇨ 750G ⇨ H2a ⇨ 4769G ⇨ H2 ⇨ 1438G ⇨ H ⇨ 152C ⇨ H(T152C)

Imperfect Match. Your results contained differences with this haplogroup:
Matches(6): 152C 263G 750G 1438G 4769G 8860G
Untested(1): 15326


2) H1(T152C)

Defining Markers for haplogroup H1(T152C):
HVR2: 152C 263G
CR: 750G 1438G 3010A 4769G 8860G 15326G
HVR1:

Marker path from rCRS to haplogroup H1(T152C):
H2a2a1(rCRS) ⇨ 263G ⇨ H2a2a ⇨ 8860G 15326G ⇨ H2a2 ⇨ 750G ⇨ H2a ⇨ 4769G ⇨ H2 ⇨ 1438G ⇨ H ⇨ 3010A ⇨ H1 ⇨ 152C ⇨ H1(T152C)

Imperfect Match. Your results contained differences with this haplogroup:
Matches(6): 152C 263G 750G 1438G 4769G 8860G
No-Calls(1): 3010A
Untested(1): 15326


3) H

Defining Markers for haplogroup H:
HVR2: 263G
CR: 750G 1438G 4769G 8860G 15326G
HVR1:

Marker path from rCRS to haplogroup H (plus extra markers):
H2a2a1(rCRS) ⇨ 263G ⇨ H2a2a ⇨ 8860G 15326G ⇨ H2a2 ⇨ 750G ⇨ H2a ⇨ 4769G ⇨ H2 ⇨ 1438G ⇨ H ⇨ 152C

Imperfect Match. Your results contained differences with this haplogroup:
Matches(5): 263G 750G 1438G 4769G 8860G
Extras(1): 152C
Untested(1): 15326


3) H69

Defining Markers for haplogroup H69:
HVR2: 152C 263G
CR: 750G 1438G 4646C 4769G 8860G 15326G
HVR1:

Marker path from rCRS to haplogroup H69:
H2a2a1(rCRS) ⇨ 263G ⇨ H2a2a ⇨ 8860G 15326G ⇨ H2a2 ⇨ 750G ⇨ H2a ⇨ 4769G ⇨ H2 ⇨ 1438G ⇨ H ⇨ 152C ⇨ H(T152C) ⇨ 4646C ⇨ H69

Imperfect Match. Your results contained differences with this haplogroup:
Matches(6): 152C 263G 750G 1438G 4769G 8860G
Mismatches(1): 4646T
Untested(1): 15326


3) H3(T152C)

Defining Markers for haplogroup H3(T152C):
HVR2: 152C 263G
CR: 750G 1438G 4769G 6776C 8860G 15326G
HVR1:

Marker path from rCRS to haplogroup H3(T152C):
H2a2a1(rCRS) ⇨ 263G ⇨ H2a2a ⇨ 8860G 15326G ⇨ H2a2 ⇨ 750G ⇨ H2a ⇨ 4769G ⇨ H2 ⇨ 1438G ⇨ H ⇨ 6776C ⇨ H3 ⇨ 152C ⇨ H3(T152C)

Imperfect Match. Your results contained differences with this haplogroup:
Matches(6): 152C 263G 750G 1438G 4769G 8860G
Mismatches(1): 6776T
Untested(1): 15326


3) H9

Defining Markers for haplogroup H9:
HVR2: 152C 263G
CR: 750G 1438G 4769G 8860G 13020C 15326G
HVR1:

Marker path from rCRS to haplogroup H9:
H2a2a1(rCRS) ⇨ 263G ⇨ H2a2a ⇨ 8860G 15326G ⇨ H2a2 ⇨ 750G ⇨ H2a ⇨ 4769G ⇨ H2 ⇨ 1438G ⇨ H ⇨ 152C ⇨ H(T152C) ⇨ 13020C ⇨ H9

Imperfect Match. Your results contained differences with this haplogroup:
Matches(6): 152C 263G 750G 1438G 4769G 8860G
Mismatches(1): 13020T
Untested(1): 15326


3) H16(T152C)

Defining Markers for haplogroup H16(T152C):
HVR2: 152C 263G
CR: 750G 1438G 4769G 8860G 10394T 15326G
HVR1:

Marker path from rCRS to haplogroup H16(T152C):
H2a2a1(rCRS) ⇨ 263G ⇨ H2a2a ⇨ 8860G 15326G ⇨ H2a2 ⇨ 750G ⇨ H2a ⇨ 4769G ⇨ H2 ⇨ 1438G ⇨ H ⇨ 10394T ⇨ H16 ⇨ 152C ⇨ H16(T152C)

Imperfect Match. Your results contained differences with this haplogroup:
Matches(6): 152C 263G 750G 1438G 4769G 8860G
Mismatches(1): 10394C
Untested(1): 15326


3) H46

Defining Markers for haplogroup H46:
HVR2: 152C 263G
CR: 750G 1438G 2772T 4769G 8860G 15326G
HVR1:

Marker path from rCRS to haplogroup H46:
H2a2a1(rCRS) ⇨ 263G ⇨ H2a2a ⇨ 8860G 15326G ⇨ H2a2 ⇨ 750G ⇨ H2a ⇨ 4769G ⇨ H2 ⇨ 1438G ⇨ H ⇨ 152C ⇨ H(T152C) ⇨ 2772T ⇨ H46

Imperfect Match. Your results contained differences with this haplogroup:
Matches(6): 152C 263G 750G 1438G 4769G 8860G
Mismatches(1): 2772C
Untested(1): 15326


3) H52

Defining Markers for haplogroup H52:
HVR2: 152C 263G
CR: 750G 1438G 4769G 8860G 14220G 15326G
HVR1:

Marker path from rCRS to haplogroup H52:
H2a2a1(rCRS) ⇨ 263G ⇨ H2a2a ⇨ 8860G 15326G ⇨ H2a2 ⇨ 750G ⇨ H2a ⇨ 4769G ⇨ H2 ⇨ 1438G ⇨ H ⇨ 152C ⇨ H(T152C) ⇨ 14220G ⇨ H52

Imperfect Match. Your results contained differences with this haplogroup:
Matches(6): 152C 263G 750G 1438G 4769G 8860G
Mismatches(1): 14220A
Untested(1): 15326

Y-DNA position(s) lacking mutations recognised by the genetic genealogy community. These Y-DNA positions may not be very useful.

## Annotation - sex and eye colour

Sex determination:

```
$ cat SNP_raw_v4_Full_20170514175358.txt | awk '{if ($2 == "Y") print $2;}' | wc -l
2129
```
Eye color determination:

```
$ cat SNP_raw_v4_Full_20170514175358.txt | awk '{if ($1 == "rs12203592" || $1 == "rs12896399" || $1 == "rs12913832" || $1 == "rs16891982" || $1 == "rs6119471") print $1,$4;}'

rs16891982 CG
rs12203592 CT
rs12896399 GG
rs12913832 AG
```
Based on this genotype, eye color is brown-green.

## Annotation of all SNPs, selection of clinically relevant ones.

```
$ awk '($32!="-") ' cIuF4BeDdMAKbTLS.txt | grep risk_factor | cut -f 1-3 | sort | uniq 
```

|ID|Position|Nucleotide|Annotation|
|--|--------|----------|----------|
|rs1024611|	17:32579788-32579788|	G|affects the production of a chemokine involved in inflammatory responses and is independently associated with an increased risk of exercise-induced ischemia, but its relevance to HIV has also been discussed|
|rs1049296|	3:133494354-133494354|	T|responsible for encoding the C1/C2 subtypes of the transferrin TF gene, with the rarer rs1049296(T) allele associated with a slightly increased risk for Alzheimer's disease and potentially reducing the effectiveness of bacterial transferrin binding proteins.|
|rs10757274|	9:22096055-22096055|	G|predictor of early myocardial infarction, as well as associated with increased risk of stroke, abdominal aortic aneurysm, and intracranial aneurysm, however it does not improve discrimination or classification of predicted heart disease risk on its own, and other SNPs in the region, such as rs2383206, can double the risk of heart disease, while rs10757278 is linked to diabetes|
|rs1169288|	12:121416650-121416650|	C|linked to lower HDL cholesterol in those with the Ile/Ile genotype and a common haplotype containing minor alleles of rs1169288 associated with lower CRP levels|
|rs12150220|	17:5485367-5485367|	T|associated with higher risk for autoimmune Addison's disease and type-1 diabetes in large patient cohorts from six different autoimmune diseases and healthy controls|
|rs13266634|	8:118184783-118184783|	T|linked to type-2 diabetes|
|rs1801197|	7:93055753-93055753|	G|Bone mineral density quantitative trait locus 15|
|rs1801274|	1:161479745-161479745|	G|associated with a variety of conditions including HIV, lymphoma, hemophilia A, malaria, and systemic lupus erythematosus, as well as with response to immunotherapeutic treatments such as cetuximab, infliximab, rituximab, and 3F8.|
|rs1801275|	16:27374400-27374400|	G|susceptibility to Atopy|
|rs1801394|	5:7870973-7870973|	G|higher risk for meningioma|
|rs1801968|	9:132580901-132580901|	G|modifier of Dystonia 1 torsion|
|rs2004640|	7:128578301-128578301|	T|associated with systemic lupus erythematosus (SLE)|
|rs2073658|	1:161010762-161010762|	T|susceptibility to Hyperlipidemia|
|rs2184026|	9:101304348-101304348|	T|susceptibility to Tobacco addiction|
|rs2239704|	6:31540141-31540141|	C|susceptibility to Leprosy|
|rs2241880|	2:234183368-234183368|	G|associated with Crohn's Disease|
|rs2281845|	1:201081943-201081943|	T|susceptibility	to Thyrotoxic periodic paralysis|
|rs231775|	2:204732714-204732714|	G|Hashimoto thyroiditis, susceptibility to Thyroid-associated orbitopathy, susceptibility to Systemic lupus erythematosus, susceptibility to Diabetes mellitus, insulin-dependent, susceptibility to Celiac disease 3|
|rs4402960|	3:185511687-185511687|	T|	Type 2 diabetes|
|rs4880|	6:160113872-160113872|	G|Microvascular complications of diabetes|
|rs4961|	4:2906707-2906707|	T|1.8x increased risk for high blood pressure|
|rs4977574|	9:22098574-22098574|	G|risk for myocardial infarction|
|rs5174|	1:53712727-53712727|	T|Myocardial infarction|
|rs5186|	3:148459988-148459988|	C|increased risk of hypertension|
|rs61747071|	16:53720436-53720436|	T|Retinitis pigmentosa in ciliopathies Joubert syndrome not specified Nephronophthisis Meckel-Gruber syndrome|
|rs6265|	11:27679916-27679916|	T|Slightly increased risk for ADHD or depression; somewhat quicker mental decline in Alzheimer patients|
|rs6280|	3:113890815-113890815|	T|Schizophrenia, susceptibility to Essential tremor, susceptibility to Hereditary|
|rs6504649|	17:48437456-48437456|	G|Pseudoxanthoma elasticum|
|rs699|	1:230845794-230845794|	G|increased risk of hypertension|
|rs763110|	1:172627498-172627498|	T|~0.80x reduced cancer risk|
|rs7794745|	7:146489606-146489606|	T|slightly increased risk for autism|
|rs909253|	6:31540313-31540313|	G|susceptibility to Myocardial infarction, Psoriatic arthritis|

