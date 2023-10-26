# Export Reports with a Subset of SNPs (optional)

Rationale: If you have multiple batches of genotyping data that used different versions of the same array, it will be possible to process these data sets together within Genvisis. However, you will first have to process/export these data separately within GenomeStudio (which will not allow idat files from different versions to be combined into the same project). Once you export each data set as FinalReport files separately, then these FinalReport files can be placed in the same directory to be imports into Genvisis. 

Best practices in this situation dictate that you should tell GenomeStudio to limit the export of each project to only those markers/probes that are present on all versions of the array that you are using. Let us know if you need help making this determination.

1. To do this, first create a 2 column, tab-delimited file with a list of SNP ids in the first column with the header Name, and a second column with a binary exclusion value (e.g. 1 = excluded, 0 = keep).
- Alternatively, you can also just include only the SNPs you want to either keep or remove. The file doesn’t need to contain every SNP in the project.
2. In the SNP Table, choose Import columns into the table from the table’s toolbar.
3. Follow the same procedure for importing rows into the Samples Table.
4. Sort on the column containing the exclusion variable you included in the imported file. If you only included a subset of SNPs in the file (eg. the SNPs you want to keep), the other SNPs will have a blank field.
5. Highlight the SNPs you want to keep, right click on them, and choose Show Only Selected Rows.
6. When you go through the report wizard, choose the option to Remove SNPs that are not visible, and then create final reports as usual.
