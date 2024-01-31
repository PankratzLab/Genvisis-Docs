# Export Reports with a Subset of SNPs (optional)

If you have multiple batches of genotyping data that used different versions of the same array, it will be possible to process these data sets together within Genvisis. However, you will first have to process and export these data separately within GenomeStudio (which will not allow ***.idat** files from different versions to be combined into the same project). After you separately export each data set to FinalReport files, these FinalReport files can be placed in the same directory to be imported into Genvisis. 

The best practice for this situation is to limit the GenomeStudio export of each project to only those markers/probes that are present on all versions of the array that you are using. Contact us if you need help making this determination. Follow these steps to limit your GenomeStudio export.

1. Create a two-column, tab-delimited file. The first column should have a **Name** header and should contain a list of SNP IDs. The second column should contain a binary exclusion value (e.g., 0=keep, 1=exclude). Alternatively, you can include only the SNPs you want to either keep or remove. The file does not need to contain every SNP in the project.
2. In the **SNP Table**, go to the toolbar and choose **Import columns into the table**.
3. Repeat the previous step to import rows into the **Samples Table**.
4. Sort on the column containing the exclusion variable in your imported file. If you included only a subset of SNPs in the file (e.g., the SNPs you want to keep), the other SNPs will have a blank field.
5. Highlight the SNPs you want to keep, right click on them, and choose **Show Only Selected Rows**.
6. When you work through the report wizard, choose the option to remove SNPs that are not visible, and then create final report files as usual.
