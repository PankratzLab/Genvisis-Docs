# Export Reports for Further Analysis in Genvisis

You must ensure that all samples are included in the Samples Table; otherwise, they will not be included in the final report files.

Go to *Analysis > Reports > Report Wizard*.
Select *Final Report > Next*, and then there are two options with two choices each. Most of the time, you will export all SNPs; if so, choose the first option for each (*Visible SNPs in the SNP Table > Include all SNPs in the report, regardless of whether or not they are visible* and *Intensity only SNPs > Include Intensity only SNPs*).

If you are exporting a subset of SNPs, use *Visible SNPs in the SNP Table > Remove SNPs that are not visible*. You will still use the *Intensity only SNPs > Include Intensity only SNPs*.

Include all of the columns that Genvisis requires:
SNP Name
Sample ID
GC Score
Allele1 - AB
Allele2 - AB
X
Y
B Allele Freq
Log R Ratio
Allele1 - Forward
Allele2 - Forward
General options
Comma
Create map files
Samples/File: 100-500 samples per file, depending on how many samples you have in your study. Genvisis is able to multithread the reading in of these files, so you can optimize this step by having at least one file per core available on the high-performance compute node that you will process this data on. If you are running a smaller number of samples on your laptop, then consider how many cores you want to allocate to Genvisis
Next > leave the default settings here > Finish (can take hours to days to run depending on the number of samples)
The FinalReport files can now be used in a Genvisis project
Genvisis can read .gz files, so the finished reports should be gzipped to save storage space.
