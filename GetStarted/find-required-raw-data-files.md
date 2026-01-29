# Find Required Raw Data Files

Genvisis requires appropriately formatted raw data files.

### Illumina GWAS Array Data

**Option 1 (best)** 
- [Create a new GenomeStudio project from raw intensity data](../#/documentation/AppendixAGenomeStudio--create-a-new-project).
- [Recluster the data in GenomeStudio](../#/documentation/AppendixAGenomeStudio--recluster-samples-before-exporting) using only the high-quality samples as seeds. Best practices recommend reclustering the data even if the project was previously processed through GenomeStudio.
- This option requires:
    - **.idat** files (several files per sample)
    - the binary manifest file for the array that was used (**.bpm** format)
    - the plain text version of the manifest file for the array (**.csv** format)

**Option 2 (next best)** 
- Open a [previously created GenomeStudio Project](../#/documentation/AppendixAGenomeStudio--open-an-existing-project).
- [Recluster using GenomeStudio](../#/documentation/AppendixAGenomeStudio--recluster-samples-before-exporting) using only the high-quality samples as seeds. Best practices recommend reclustering the data even if the project was previously processed through GenomeStudio.
- This option requires:
    - a BeadStudio/GenomeStudio (**.bsc**) file
    - the contents of the GenomeStudio **Data/** directory
    - the plain text version of the manifest file for the array (**.csv** format)

**Option 3 (last resort)** 
- Use existing Illumina Final Report files. 
- This option requires:
    - final report files with one or more samples per file (see below)
    - the plain text version of the manifest file for the array (**.csv** format)

    The final report files must include several columns: SNP name, Sample ID, GC score, Allele1 - AB, Allele2 - AB, X, and Y. Two optional but helpful columns are B allele frequency and Log R ratio.


Note that, for any of these options, the Illumina manifest file must contain probe sequences for Genvisis to be able to run the **[Run Marker BLAST Annotation](../#/documentation/RunTheGenvisisWorkflow--run-marker-blast-annotation-illumina)** workflow step. Generally it is possible to find a manifest file that contains probe sequences; we recommend contacting Illumina if you need assistance. As described in **[Run Marker BLAST Annotation](../#/documentation/RunTheGenvisisWorkflow--run-marker-blast-annotation-illumina)**, if you do not have a probe set file, uncheck the **[Run Marker BLAST Annotation](../#/documentation/RunTheGenvisisWorkflow--run-marker-blast-annotation-illumina)** box in the Genvisis workflow.

### Affymetrix Data (Affy6/Axiom)
For Affymetrix data, Genvisis requires the following:
- **.CEL** files (one per sample)
- Affymetrix Power Tools
- Affymetrix Annotation file (**.annot.csv**) aka manifest (Genvisis comes with **GenomeWideSNP_6.na35.annot.csv**, which works for most Affymetrix projects)

Optionally, you can include an Affymetrix Probe Set file (**.probe_tab**). This file is required for the **[Run Marker BLAST Annotation](../#/documentation/RunTheGenvisisWorkflow--run-marker-blast-annotation-affymetrix)** step of the Genvisis workflow. 

The Affy6 probe set file is saved in the [Genvisis resources directory](../#/documentation/GetStarted--resources-directory). 

ThermoFisher no longer shares Affymetrix probe sequences, so probe set files for Axiom arrays may be unavailable. As described in **[Run Marker BLAST Annotation](../#/documentation/RunTheGenvisisWorkflow--run-marker-blast-annotation-affymetrix)**, if you do not have a probe set file, uncheck the **[Run Marker BLAST Annotation](../#/documentation/RunTheGenvisisWorkflow--run-marker-blast-annotation-affymetrix)** box in the Genvisis workflow.
