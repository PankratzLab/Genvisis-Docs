# Find Required Raw Data Files

Genvisis requires appropriately formatted raw data files.

## Illumina GWAS Array Data
**Option 1 (best):** 
    * [Create a new GenomeStudio project from raw intensity data](../#/documentation/AppendixAGenomeStudio--create-a-new-project).
    * [Recluster the data in GenomeStudio](../#/documentation/AppendixAGenomeStudio--recluster-samples-before-exporting) using only the high-quality samples as seeds. 
     * Best practices recommend reclustering the data even if the project was previously processed through GenomeStudio.
    * This option requires:
     * .idat files (several files per sample)
     * The binary manifest file for the array that was used (.bpm format)
     * The plain text version of the manifest file for the array (.csv format)

**Option 2 (next best):** 
    * Open a [previously created GenomeStudio Project](../#/documentation/AppendixAGenomeStudio--open-an-existing-project).
    * [Recluster using GenomeStudio](../#/documentation/AppendixAGenomeStudio--recluster-samples-before-exporting) using only the high-quality samples as seeds. 
     * Best practices recommend reclustering the data even if the project was previously processed through GenomeStudio.
    * This option requires:
     * A BeadStudio/GenomeStudio (.bsc) file
     * The contents of the GenomeStudio **Data/** directory
     * The plain text version of the manifest file for the array (.csv format)

**Option 3 (last resort):** 
    * Use existing Illumina Final Report files. 
    * This option requires:
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
    * .CEL files (one per sample)
    * Affymetrix Power Tools
    * Affymetrix Annotation file (*.annot.csv) aka Manifest
     * Genvisis comes with **GenomeWideSNP_6.na35.annot.csv**, which works for most Affymetrix projects
    * (optional) Affymetrix Probe Set file (*.probe_tab)
     * Found inside Affymetrix Power Tools
     * /CD\_GenomeWideSNP\_6\_rev3/Full/GenomeWideSNP\_6/LibFiles/GenomeWideSNP\_6.probe\_tab
