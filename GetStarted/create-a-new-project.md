# Create a New Project

1. Create a directory for your project (written as **[ProjectDir]** for the rest of this documentation).
2. Within **[ProjectDir]**, create a subdirectory for the raw data; internally we use the naming convention **00src** (i.e., **[ProjectDir]/00src**), but this is not mandatory.
3. Within **00src**, place either the FinalReport files from GenomeStudio (either **.csv** or **.csv.gz** format) or Affymetrix .CEL files. Only Final Report or .CEL files should be in this directory. [Click here](https://docs.google.com/document/d/1BMu1zp8er9NY-QFRh-7ZOeX1HnGj_yAYYh3BarASwPY/edit#bookmark=id.2ab481w48low) for a tutorial on how to process a project using GenomeStudio. [Click here](https://docs.google.com/document/d/1BMu1zp8er9NY-QFRh-7ZOeX1HnGj_yAYYh3BarASwPY/edit#bookmark=kix.rnqrxmj63otl) for a tutorial on how to recluster data using only the high-quality samples as seeds. Best practices recommend reclustering the data even if the project was previously processed through GenomeStudio.
4. In **[ProjectDir]**, place
    * (Illumina only) The **.csv** version of the project’s **manifest file** (with probe sequences)
    * [**pedigree.txt** and **linker.txt**](#bookmark=id.3wqz7fyhw1k7) (within a data subdirectory (i.e., **[ProjectDir]/data**))
    * If your samples were processed in batches, **batch.text** [within a data subdirectory (i.e., **[ProjectDir]/data**)] listing sample IDs and batch names (no header) so Genvisis can control for batch effects. For example:

            ID001	California
            ID002 California
            ID003	NBS
            ID004	NBS
            ID005	COG
            ID006	COG

    * (Illumina only) If available, the **SNP_Map.csv** file that was produced by GenomeStudio at the same time as the reports. This is necessary only if your manifest does not contain probe sequences.
5. Once the directories are set up and the necessary files are in place, run **genvisis.jar**.
    * Linux/Mac
        * Open a terminal and run **java -Xmx#g -jar [path]/genvisis.jar**
         * #g is the number of gigabytes of memory
         * [path] is the location of the genvisis.jar file
         * e.g., **java -Xmx24g -jar ~/genvisis.jar** (if **genvisis.jar** is saved in your home directory)
        * Alternatively, locate **genvisis.jar** within a file manager and double-click on the Genvisis icon
    * Windows
        * Open a text file and write **java -Xmx#g -jar genvisis.jar**
         * #g is the number of gigabytes of memory
        * Save the text file as **vis.bat** in the same directory as **genvisis.jar**
        * Double-click **vis.bat**
6. In the Genvisis window that opens, click **File** → **New Project**
7. Enter a **Project Name**
8. Click **...** next to **Project Directory**
9. Choose the **[ProjectDir]** → **Select**
10. Click **...** next to **Source File Directory**
11. Choose the **00src** directory created earlier → **Select**
12. Genvisis will automatically detect the number of source files and the extension (eg. .csv, .csv.gz, .CEL, etc.).
13. Choose the **Array Type** with which the data was collected:
    * ILLUMINA
    * AFFY_GW6
        * Only SNP probesets
    * AFFY_GW6_CN
        * SNP probesets plus copy number probesets
    * NGS_WES
    * NGS_WGS
    * AFFY_AXIOM
    * If you choose one of the Affymetrix arrays, there will an additional option, Start From. Select the appropriate option:
        * CEL files
        * APT results
            * Must have the same name as the **Project Name**
14. **Genome Build** allows you to specify which version of the human genome to run the project in (e.g., **[Genome Reference Consortium Human Build 38](https://www.ncbi.nlm.nih.gov/assembly/GCF_000001405.26/)** aka **GRCh38**). 
    * Unless there is a specific need to use an older version of the genome, set **Genome Build** to **hg38**, even if the manifest is in an older build. Genvisis can liftover marker positions to **hg38** in the [Create Marker Positions](#bookmark=id.n8xlweakplyx) step of the Workflow.
    * To determine which version of the genome your data is in, check the **GenomeBuild** column of your manifest.
15. Select locations for the following files:
    * **Pedigree file**
    * **Sample ID linker file**
    * **Batch file**
    * **Marker subset file [optional]**
        * Used only if you are not analyzing all markers in the manifest
16. If using Illumina reports, **Create** will launch the **Validation Review** window. Fields will be automatically populated from the source files.
    * **Allele 1/2 - Genotype:** These are important when combining data sets from multiple sources. In that case, a reference genome with a reference allele and an alternate allele are necessary. Illumina doesn't use that designation, so the categories used here for Illumina reports don't matter too much (can be forward allele or top allele designations).
    * **Allele 1/2 - AB:** This is more important than Allele 1/2 - Genotype. The genotype can either be AA, BB, AB, or missing.
    * **X/Y:** This is intensity data. If you want to do anything with Copy Number Variation calling or review cluster plots, this is necessary. What sets Genvisis apart is its ability to review raw data. X/Y are the most important variables followed by the Allele 1/2 AB genotype.
    * **B Allele Frequency and Log-R Ratio:** Genvisis can compute these from X and Y, so it's not critical to import these, but you can import them if they're available in the report.
    * **Confidence:** An optional category that is useful if you have only genotypes and no raw intensity data (X/Y). Defaults to GC score. The confidence score can be used to set a higher threshold than what the GenomeStudio report originally produced.
17. If the reports don’t have consistent headers, there will be a separate validation review window for each group of reports.
18. Click **OK. **A new window will appear: **[Genvisis Project Workflow](#bookmark=id.s30o3wuyykva)**
19. If using Affymetrix CEL files, there will be no Validation Review and Genvisis will go directly to the Project Workflow.
20. Inside **[ProjectDir]**, two new directories will appear: **data/** and **logs/**. A file named **source_headers.ser** will also appear in **[ProjectDir]**.
