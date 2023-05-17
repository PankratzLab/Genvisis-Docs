# Set Up Pedigree and Linker

Genvisis projects require a **pedigree.txt** file containing unique subject ids and a **linker.txt** file that identifies duplicate subjects.

1. Create **pedigree.txt** and save this file in **[ProjectDir]/data/**. This file must contain a header and the following columns: **FID IID	FA	MO	SEX	AFF**
    * The structure is identical to the [plink.fam](https://www.cog-genomics.org/plink2/formats#fam) file format.
    * **FID** and **IID** are the family and individual IDs.
    * **FA** is the **IID** of the sample’s father (**0** if parent not in dataset).
    * **MO** is the **IID** of the sample’s mother (**0** if parent not in dataset).
    * **SEX** is 1 for male or 2 for female (if GenomeStudio can’t determine sex and you don’t have phenotype data, use **0** then update the pedigree manually after running the **[Sex Checks](#bookmark=id.ffdnn8hxfe09)** step in Genvisis).
    * **AFF** or **PHENO **(Affected or Phenotype)** is 2 (for a case), 1 (for a control), or either 0 or -9 (for unknown); this column is not used much except for PLINK/VCF export and for filtering out markers that have a call rate that differs by this affected status.
    * **mzTwinID** (monozygotic twins) is an optional final column (any additional columns beyond this will be ignored). The ID number in this column should be the same for both/all samples in a given mzTwin set (e.g. the first set both coded as 1, the second set coded all as 2, etc). For non-mzTwins the column should contain a period.
    * If siblings are present in the dataset, but not their parents, dummy IDs can be created in the **IID** column that share **FID** with the siblings. The dummy IDs can then be listed under **FA** and **MO** for the siblings. The dummy IDs do not need to be included in the Linker file.
    * Note: the pedigree should be shorter than the total number of samples if duplicates are present. The pedigree should contain only unique IIDs with **Linker.txt** handling duplicate samples.
2. Create a **Linker.txt** file and save this file in **[ProjectDir]/data/**. This file must contain a header and the following columns: **DNA	FID	IID**
    * The **DNA** column must match the **Sample ID** used in GenomeStudio. The GenomeStudio **Sample ID** is used to name the **.sampRAF** files and Genvisis matches the **DNA** column in **Linker.txt** to the **.sampRAFs**.
    * **FID** and **IID** can have duplicates, but each **DNA** ID must be unique.
    * If making a **Linker.txt** file in Excel, set the format of the columns to **Text** before adding the IDs (the default is **General**, where Excel will guess the format of each value). IDs that are solely numbers will have leading zeros removed by Excel in this situation, which will lead to Genvisis not being able to match those rows in the **Linker.txt** file with the corresponding **.sampRAFs**. It is best to copy **Sample IDs** directly from the GenomeStudio project and not the **Sample_Map.csv** that is produced with reports, as opening **Sample_Map.csv** in Excel automatically removes leading zeros.
3. Genvisis projects created prior to August 2021 may have issues using linker and pedigree, specifically, you may see a checksums failure when loading linker or pedigree. To resolve this issue, re-run the GWAS_QC step of the workflow. Genvisis should add a checksum to the first line of the relationshipChecks.xln file. You may need to remove/back-up your existing relationship checks.
