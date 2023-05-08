## Required Raw Data Files


### For Affymetrix Data (Affy6/Axiom)
.CEL files (one per sample, may be gzipped as .CEL.gz)
Affymetrix Annotation file (*.annot.csv) aka Manifest
(optional) Affymetrix Probe Set file (*.probe_tab)


### For Illumina GWAS Array Data
**Option 1 (preferred)**
Start with raw intensity data and [recluster using GenomeStudio](https://docs.google.com/document/d/1BMu1zp8er9NY-QFRh-7ZOeX1HnGj_yAYYh3BarASwPY/edit#bookmark=kix.rnqrxmj63otl). This option requires

* .idat files (several files per sample)
* .bpm file (the binary manifest file for the array that was used)

**Option 2 (next best)**
Start with a GenomeStudio Project and [recluster using GenomeStudio](https://docs.google.com/document/d/1BMu1zp8er9NY-QFRh-7ZOeX1HnGj_yAYYh3BarASwPY/edit#bookmark=kix.rnqrxmj63otl). This option requires

* A BeadStudio/GenomeStudio (.bsc file)
* The contents of the GenomeStudio Data/ directory
* The corresponding manifest file for the array (.bpm or .csv format)

**Option 3 (last resort)**
Use existing Illumina Final Report files. This option requires

* Final Report files with one or multiple samples per file. At a minimum, they must contain the following columns:
    * SNP Name
    * Sample ID
    * GC Score
    * Allele1 - AB
    * Allele2 - AB
    * X
    * Y
    * (optional, but helpful) B Allele Freq
    * (optional, but helpful) Log R Ratio
    * The corresponding manifest file for the array (.bpm or .csv format) \
