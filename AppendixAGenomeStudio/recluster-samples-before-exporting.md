# Recluster Samples Before Exporting to Genvisis

1. To create reports for use in Genvisis projects, first recluster SNPs based only on “high quality” samples.
    * High quality is determined from the Callrate in the Samples Table
2. Click on the Callrate column (it will highlight yellow), and then Sort column option on the toolbar directly above.
3. Highlight low quality samples to exclude (click on the first row to exclude, hold down shift, and then click on the last row).
    * For Illumina data, choose samples < 0.98
    * These are hard cutoffs. 0.97999 call rates will be excluded.
    * The one exception to these values is if < 0.98 will exclude a large percentage of samples. If this is the case then consider a lower threshold, perhaps 0.95. This is especially appropriate if you have markers that have been zeroed out in GenomeStudio (i.e., everyone has a missing genotype)
4. Right click on the highlighted samples > Exclude Selected Samples
5. A pop-up window will ask Do you wish to update statistics for all SNPs? Choose No
6. Now you can recluster SNPs using only the high quality samples.
    * On the toolbar, choose Analysis > Cluster all snps
    * Tip: Reclustering snps can take many hours or even days depending on the size of the dataset. GenomeStudio can’t be minimized during this. To keep working on the same machine, you can create new Desktops on Windows by clicking Task View next to the search bar.
    * If you only need to recluster individual SNPs and not all of them, you can right click in the Full Data Table > Cluster Selected SNP
    * Clicking in the Full Data Table will also cause the SNP Graph to appear in the upper left, showing where all the samples fall for a particular SNP.
7. After all SNPs have been reclustered, you’ll need to recluster the Y chromosome
In the Samples Table, the Gender column will list all samples as Unknown.
Highlight all samples > Right click > Estimate gender for selected samples > "Would you like to populate the Gender column (as well as the GenderEst column) with the result of the calculation?" > Yes
Explanation of how GenomeStudio determines sex
Go to the central table and choose the SNP Table tab
Sort column (Ascending) by Call Freq
Click on any Y chromosome marker
You’ll notice a large clump of samples along the x-axis in the SNP Graph. These are females, who don’t provide a value when chrY is measured.
It’s possible that one of the clusters may be centered around the females. This is a problem. Females and samples with unknown sex need to be temporarily excluded and chrY reclustered.
Sort by Gender in the Samples Table and then exclude Females, Unknowns, and low call rate Males
Back in SNP Table, filter to only show chrY
Click the Filter rows icon on the toolbar below the SNP Table tab
In the pop-up window, choose Chr under Column, set Operation to =, enter Y in the Value field, and click the ==> below it.
If a value is already in the Filter Tree View, clear Clear All at the bottom to remove the old value
Click OK
Back in the SNP Table, only rows for chrY will now be listed.
Highlight all SNPs for chrY > right click in the SNP Table > cluster selected SNPs
After it finishes running, a pop-up window will ask “Do you wish to update SNP statistics for the selected SNPs?” Choose No
Check the SNP Graph for various SNPs on chrY and you should now see 1-2 proper clusters without influence from the females and unknowns
