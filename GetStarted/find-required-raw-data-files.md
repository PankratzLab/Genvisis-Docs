# Find Required Raw Data Files

Genvisis requires appropriately formatted raw data files.

## For Illumina GWAS Array Data

**Option 1 (best):** Start with raw intensity data and [recluster using GenomeStudio](https://docs.google.com/document/d/1BMu1zp8er9NY-QFRh-7ZOeX1HnGj_yAYYh3BarASwPY/edit#bookmark=kix.rnqrxmj63otl). This option requires both
* .idat files (several files per sample) and
* A .bpm file (the binary manifest file for the array that was used).

**Option 2 (next best):** Start with a GenomeStudio Project and [recluster using GenomeStudio](https://docs.google.com/document/d/1BMu1zp8er9NY-QFRh-7ZOeX1HnGj_yAYYh3BarASwPY/edit#bookmark=kix.rnqrxmj63otl). This option requires all of the following:
* A BeadStudio/GenomeStudio (.bsc) file,
* The contents of the GenomeStudio *Data/* directory, and
* The corresponding manifest file for the array (.bpm or .csv format).

**Option 3 (last resort):** Use existing Illumina Final Report files. This option requires
* Final report files with one or multiple samples per file. These files must contain the following columns:
    * SNP name
    * Sample ID
    * GC score
    * Allele1 - AB
    * Allele2 - AB
    * X
    * Y
    * B allele frequency (optional, but helpful)
    * Log R ratio (optional, but helpful)
* The corresponding manifest file for the array (.bpm or .csv format)

## For Affymetrix Data (Affy6/Axiom)

For Affymetrix data, Genvisis requires the following:
* .CEL files (one per sample, may be gzipped as .CEL.gz)
* Affymetrix Annotation file (*.annot.csv) aka Manifest
* (optional) Affymetrix Probe Set file (*.probe_tab)
