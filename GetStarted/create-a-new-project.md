# Create a New Project

1. Once the directories are set up and the necessary files are in place, run **genvisis.jar**.
    * Linux/Mac/Running remotely on Linux
        * Open a terminal and run **java -Xmx#g -jar [path]/genvisis.jar**
         * **#g** is the number of gigabytes of memory to use
         * [path] is the location of the genvisis.jar file
         * Example
             * **java -Xmx24g -jar ~/genvisis.jar** (if **genvisis.jar** is saved in your home directory)
        * Alternatively, locate **genvisis.jar** within a file manager and double-click on the Genvisis icon
    * Windows
        * Open a text file and write inside **java -Xmx#g -jar genvisis.jar**
        * **#g** is the number of gigabytes of memory to use
        * Example
            * **java -Xmx24g -jar genvisis.jar**
        * Save the text file as **vis.bat** in the same directory as **genvisis.jar**
        * Double-click **vis.bat**

![Image of Genvisis opened for the first time](/Images/GenvisisOpened.png)

6. In the Genvisis window that opens, click **File** → **New Project**

![Image of the Genvisis project creation window](/Images/NewProjectCreationWindow.png)

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
    * If you choose one of the Affymetrix arrays, there will be the additional option **Start From**:
        * CEL files
        * APT results
            * Must have the same name as the **Project Name**
14. **Genome Build** allows you to specify which version of the human genome to run the project in (e.g., **[Genome Reference Consortium Human Build 38](https://www.ncbi.nlm.nih.gov/assembly/GCF_000001405.26/)** (external link) aka **GRCh38**). 
    * Unless there is a specific need to use an older version of the genome, set **Genome Build** to **HG38**, even if the manifest is in an older build. Genvisis can remap marker positions to **hg38** in the [Create Marker Positions](../#/documentation/RunTheGenvisisWorkflow--create-marker-positions-illumina) step of the Workflow.
    * To determine which version of the genome your data is in, check the **GenomeBuild** column of your Illumina manifest, or the header of your Affymetrix manifest.
15. Select the locations for the following files:
    * **Illumina Manifest File** (if applicable)
    * **Pedigree File**
    * **Sample ID Linker File**
    * **Batch File**
    * **Marker Subset File**
        * Used only if you are not analyzing all markers in the manifest
16. If using Illumina reports, **Create** will launch the **Validation Review** window. Fields will be automatically populated from the source files.
    * Required
        * **Marker Name**
        * **Sample ID**
    * Recommended
        * **Allele 1/2 - ACGT Genotype:** These are important when combining data sets from multiple sources. In that case, a reference genome with a reference allele and an alternate allele are necessary. Illumina doesn't use that designation, so the categories used here for Illumina reports don't matter too much (can be forward allele or top allele designations).
        * **Allele 1/2 - AB Genotype:** This is more important than Allele 1/2 - Genotype. The genotype can either be AA, BB, AB, or missing.
        * **X/Y:** This is intensity data. If you want to do anything with Copy Number Variation calling or review cluster plots, this is necessary. What sets Genvisis apart is its ability to review raw data. X/Y are the most important variables followed by the Allele 1/2 AB genotype.
        * **B Allele Frequency** and **Log-R Ratio:** Genvisis can compute these from X and Y, so it's not critical to import these, but you can import them if they're available in the report.
        * **Confidence:** An optional category that is useful if you have only genotypes and no raw intensity data (X/Y). Defaults to GC score. The confidence score can be used to set a higher threshold than what the GenomeStudio report originally produced.
    * Optional
        * **X/Y Raw**
        * **R**
        * **Theta**

![Image of the Validation Review window](/Images/ValidationReview.png)

17. If the reports don’t have consistent headers, there will be a separate validation review window for each group of reports.
18. Click **OK**. 
19. An audit will be performed to verify that the markers in the manifest are either 100% congruent with one of the reports, or that both the manifest and a report are 100% congruent with the Marker Subset File if one is provided.
* If the manifest and the examined report match, a new project will be created and a new window will appear: **[Genvisis Project Workflow](../#/documentation/RunTheGenvisisWorkflow--introduction-to-the-workflow)**
* If the manifest and examined report do not match, project creation will fail and you will need to create a Marker Subset File that lists only the markers shared between both files.
20. If using Affymetrix CEL files, there will be no Validation Review and Genvisis will go directly to the **[Project Workflow](../#/documentation/RunTheGenvisisWorkflow--introduction-to-the-workflow)**.
21. Several new files will be generated.  Inside **[ProjectDir]** will be a file named **source_headers.ser** and the new sub-directory **logs/**.  Inside **data/** will be the file **import.ser**.
