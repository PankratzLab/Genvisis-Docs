# Recluster Samples Before Exporting to Genvisis

To create reports for use in Genvisis projects, first recluster SNPs based on only high quality samples (as determined by the **Callrate** in the **Samples Table**).

1. Click on the **Callrate** column (it will be highlighted yellow) and then the **Sort column** option on the toolbar directly above.
2. Highlight low quality samples to exclude (click on the first row to be excluded, hold down the shift key, and then click on the last row).
    * For Illumina data, choose samples **<0.98**.
    * Note that this value is a hard cutoff. For example, a sample with a call rate of 0.97999 will be excluded.
    * The one exception to these values is if **<0.98** will exclude a large percentage of samples. If this is the case then consider a lower threshold, perhaps **0.95**. This is especially appropriate if you have markers that have been zeroed out in GenomeStudio (i.e., if everyone has a missing genotype).
3. Right click on the highlighted samples and then select **Exclude Selected Samples**.
4. A pop-up window will ask **Do you wish to update statistics for all SNPs?** Choose **No**.
5. Now you can recluster SNPs using only the high quality samples. On the toolbar, choose **Analysis > Cluster all snps**.
    * Tip: Reclustering SNPs can take hours or even days depending on the size of the dataset. GenomeStudio cannot be minimized during this process. To keep working on the same (Windows) machine, you can create a new Desktop by clicking **Task View** (next to the search bar).
    * Tip: If you need to recluster only individual SNPs (not all SNPs), right click in the **Full Data Table > Cluster Selected SNP**.
    * Tip: Click in the full data table to see the SNP graph in the upper left. This graph shows where all samples fall for a particular SNP.
6. After all SNPs have been reclustered, you need to recluster the Y chromosome.
    A. In the **Samples Table**, the **Gender** column will list all samples as **Unknown**. Highlight all samples, right click, and then select **Estimate gender for selected samples**.
    B. For **Would you like to populate the Gender column (as well as the GenderEst column) with the result of the calculation?**, select **Yes**.
        * Tip: [See below for an explanation of how GenomeStudio determines sex](https://genvisis.org/#/documentation/AppendixAGenomeStudio--sex-determination-explained)
    C. Go to the central table and choose the **SNP Table** tab.
    D. Sort column (ascending) by **Call Freq**.
    E. Click on any Y chromosome marker.
        * You will notice a large clump of samples along the x-axis in the SNP Graph. These are females, who do not provide a value when chrY is measured.
        * It is possible that one of the clusters may be centered around the females. This is a problem. Females and samples of unknown sex need to be temporarily excluded and chrY reclustered.
7. In the **Samples Table**, sort by **Gender** and then exclude females, unknowns, and low call rate males.
8. Back in the **SNP Table**, filter to show only chrY.
    A. Click the **Filter rows** icon on the toolbar (below the **SNP Table** tab).
    B. In the pop-up window, set **Column** to **Chr**, set **Operation** to **=**, set **Value** to **Y**, and click **==>**.
    C. If a value is already in the **Filter Tree View**, clear **Clear All** at the bottom to remove the old value. Click **OK**.
9. Back in the **SNP Table**, only rows for chrY will now be listed.
    A. Highlight all SNPs for chrY, right click in the SNP Table, and cluster selected SNPs.
    B. A pop-up window will ask **“Do you wish to update SNP statistics for the selected SNPs?”** Choose **No**.
10. Check the **SNP Graph** for various SNPs on chrY. Now you should see one or two proper clusters without influence from the females and unknowns.
