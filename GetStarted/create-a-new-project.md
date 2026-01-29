# Create a New Project in Genvisis

To create a new project, open Genvisis and then go to **File** → **New Project**.

![Image of Genvisis opened for the first time](/Images/GenvisisOpened.png)

![Image of the Genvisis project creation window](/Images/NewProjectCreationWindow.png)

1. Enter a **Project Name**
2. Click **...** next to **Project Directory**
3. Choose the **[ProjectDir]** → **Select**
4. Click **...** next to **Source File Directory**
5. Choose the **00src** directory created earlier → **Select**
6. Genvisis will automatically detect the number of source files and the extension (e.g., **.csv**, **.csv.gz**, **.CEL**, etc.)
7. Choose the **Array Type** with which the data was collected:
    - ILLUMINA
    - AFFY\_GW6
        - Only SNP probesets
    - AFFY\_GW6\_CN
        - SNP probesets plus copy number probesets
    - NGS\_WES
    - NGS\_WGS
    - AFFY\_AXIOM
    - If you choose one of the Affymetrix arrays, there will be the additional option **Start From**:
        - CEL files
        - APT results (must have the same name as the **Project Name**)
8. **Genome Build** allows you to specify which version of the human genome to run the project in (e.g., **[Genome Reference Consortium Human Build 38](https://www.ncbi.nlm.nih.gov/assembly/GCF_000001405.26/)** (external link), which is also known as **GRCh38**). Unless there is a specific need to use an older version of the genome, set **Genome Build** to **HG38**, even if the manifest is in an older build. Genvisis can remap marker positions to **hg38** in the [Create Marker Positions](../#/documentation/RunTheGenvisisWorkflow--create-marker-positions-illumina) step of the Workflow.
    - To determine genome version of your data, check the **GenomeBuild** column of your Illumina manifest or the header of your Affymetrix manifest.
9. Select the locations for the following files:
    - **Illumina Manifest File** (if applicable)
    - **Pedigree File**
    - **Sample ID Linker File**
    - **Batch File**
    - **Marker Subset File**
        - Used only if you are not analyzing all markers in the manifest
10. If using Illumina reports, **Create** will launch the **Validation Review** window. Fields will be automatically populated from the source files.
    - Required
        - **Marker Name**
        - **Sample ID**
    - Recommended
        - **Allele 1/2 - ACGT Genotype:** These are important when combining data sets from multiple sources. In that case, a reference genome with a reference allele and an alternate allele are necessary. Illumina does not use that designation, so the categories used here for Illumina reports do not matter too much (can be forward allele or top allele designations).
        - **Allele 1/2 - AB Genotype:** This is more important than Allele 1/2 - Genotype. The genotype can either be AA, BB, AB, or missing.
        - **X/Y:** This is intensity data. If you want to do anything with copy number variation calling or review cluster plots, this is necessary. What sets Genvisis apart is its ability to review raw data. X/Y are the most important variables followed by the Allele 1/2 AB genotype.
        - **B Allele Frequency** and **Log-R Ratio:** Genvisis can compute these from X and Y, so it is not critical to import these, but you can import them if they are available in the report.
        - **Confidence:** An optional category that is useful if you have only genotypes and no raw intensity data (X/Y). Defaults to GC score. The confidence score can be used to set a higher threshold than what the GenomeStudio report originally produced.
    - Optional
        - **X/Y Raw**
        - **R**
        - **Theta**

![Image of the Validation Review window](/Images/ValidationReview.png)

11. If the reports do not have consistent headers, there will be a separate validation review window for each group of reports.
12. Click **OK**. 
13. An audit will be performed to verify that the markers in the manifest are either 100% congruent with one of the reports, or that both the manifest and a report are 100% congruent with the Marker Subset File if one is provided.
    - If the manifest and the examined report match, a new project will be created and a new window will appear: **[Genvisis Project Workflow](../#/documentation/RunTheGenvisisWorkflow--introduction-to-the-workflow)**
    - If the manifest and examined report do not match, project creation will fail and you will need to create a Marker Subset File that lists only the markers shared between both files.
14. If using Affymetrix CEL files, there will be no Validation Review and Genvisis will go directly to the **[Project Workflow](../#/documentation/RunTheGenvisisWorkflow--introduction-to-the-workflow)**.
15. Genvisis will generate several new files. Inside **[ProjectDir]** will be a file named **source_headers.ser** and the new sub-directory **logs/**. Inside **data/** will be a new **import.ser** file.
