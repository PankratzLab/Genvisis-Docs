# Create Pedigree and Linker Files

Genvisis requires a **pedigree.txt** file, which contains unique subject IDs, and a **linker.txt** file, which identifies duplicate subjects.

## Pedigree
Create **pedigree.txt**. This file must contain a header and the following columns: FID, IID, FA, MO, SEX, and AFF. The format of **pedigree.txt** is identical to format of [plink.fam](https://www.cog-genomics.org/plink2/formats#fam) (external link).
- **FID** and **IID** are the family and individual IDs.
- **FA** is the **IID** of the sample’s father (**0** if the parent is not in the dataset).
- **MO** is the **IID** of the sample’s mother (**0** if the parent is not in the dataset).
- **SEX** is **1** for male and **2** for female (if GenomeStudio can’t determine sex and you don’t have phenotype data, use **0** then update the pedigree manually after running the **[Sex Checks](../#/documentation/RunTheGenvisisWorkflow--run-sex-checks)** step in Genvisis).
- **AFF** or **PHENO** (Affected or Phenotype) is **2** for a case, **1** for a control, and either **0** or **-9** for unknown. This column is used when exporting PLINK and VCF files, and during CNV analysis.
- **mzTwinID** (monozygotic twins) is an optional final column. Any additional columns beyond **mzTwinID** will be ignored. The ID number in this column should be the same for both/all samples in a given mzTwin set (e.g. the first set both coded as **1**, the second set coded all as **2**, etc). For non-mzTwins the column should contain a period.
- If siblings are present in the dataset, but not their parents, dummy IDs can be created in the **IID** column that share **FID** with the siblings. The dummy IDs can then be listed under **FA** and **MO** for the siblings. The dummy IDs do not need to be included in the linker file described below.

Note: if duplicates are present, the pedigree file should be shorter than the total number of samples. The pedigree should contain only unique IIDs (**linker.txt**, described below, deals with duplicate samples).

## Linker
Create **linker.txt**. This file must contain a header and the following columns: DNA, FID, and IID.
- The IDs in the **DNA** column must match either the **Sample ID** used in GenomeStudio or the names of the Affymetrix **.CEL** files. The GenomeStudio **Sample ID**/Affymetrix **.CEL** file is used to name the sample files (**.sampRAF**) that Genvisis creates from the raw data files. The **DNA** column in **linker.txt** is used to match these new sample files to the **FID IID** columns in the pedigree.
- If the same subject is present multiple times in a study, list each of its unique sample IDs under the **DNA** column, with the same **FID IID** for each sample.
- Example
            DNA    FID  IID 
            ID001  NA1  NA8
            ID002  NA1  NA8
            ID003  NA1  NA8
       
- Each **DNA** ID in a linker file must be unique. Only the **FID IID** column can have duplicate values.

Note: If you create pedigree and linker files in Excel, set the format of the columns to **Text** before adding the IDs. The default format is **General**, where Excel will guess the format of each value; with the **General** format, Excel will strip leading zeroes from numerical IDs [e.g., 0000034 becomes 34], which will lead to Genvisis not being able to match the pedigree and linker IDs with the IDs in the report files. In Illumina projects, it is best to copy the Sample IDs directly from the GenomeStudio project and not from the **Sample\_Map.csv** file that is produced with reports, as opening **Sample\_Map.csv** in Excel automatically removes leading zeros.
