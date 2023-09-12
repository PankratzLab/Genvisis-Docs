# Find Required Raw Data Files

Genvisis requires appropriately formatted raw data files.

## Illumina GWAS Array Data
**Option 1 (best):** Start with raw intensity data and 
[recluster using GenomeStudio](../#/documentation/AppendixAGenomeStudio--recluster-samples-before-exporting.md). 
This option requires both:
* .idat files (several files per sample) and
* The binary manifest file for the array that was used (.bpm format).
* The plain text version of the manifest file for the array (.csv format).

**Option 2 (next best):** Start with a pre-existing GenomeStudio Project and
[recluster using GenomeStudio](../#/documentation/AppendixAGenomeStudio--recluster-samples-before-exporting.md). This option requires all of the following:
* A BeadStudio/GenomeStudio (.bsc) file,
* The contents of the GenomeStudio **Data/** directory, and
* The plain text version of the manifest file for the array (.csv format).

**Option 3 (last resort):** Use existing Illumina Final Report files. This option requires both:
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
* The plain text version of the manifest file for the array (.csv format).

## Affymetrix Data (Affy6/Axiom)
For Affymetrix data, Genvisis requires the following:
* .CEL files (one per sample, may be gzipped as .CEL.gz)
* Affymetrix Annotation file (*.annot.csv) aka Manifest
* (optional) Affymetrix Probe Set file (*.probe_tab)
