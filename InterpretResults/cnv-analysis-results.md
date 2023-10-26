# Interpret CNV Analysis Results

After running the [CNV Analysis Pipeline](../#/documentation/RunTheGenvisisWorkflow--run-cnv-analysis-pipeline), the **[ProjectDir]/cnv\_analysis/Filtered\_Samples/** directory (Filtered\_Samples may have a different name if you used a different label for the .fam file) contains 5 sub-directories, one for each model.  There are 28 output files in each of these, but the ones most relevant for analysis (**.confPosition.out** and **.confWindow.out.**) have copies in the **cnv\_analysis/results/** directory.

In **.confPosition.out**, sort the columns by **EMP2** from smallest to largest.  **EMP1** is the locus level p-value and **EMP2** is the genome wide p-value.  The CNVs have been compared against the breakpoints in the **.conf.cnv.map** file in each model directory.  If any **EMP2** values are less than 0.05, you will need to visualize the regions to verify if they're true positives or not:

1. In **.confPosition.out**, create a list of significant regions using the first and last SNPs on a chr that are EMP2 < 0.05 and store them in a new text file. For example:

            chr7:31550705-31552108
            chr10:18550421-18572274
            chr11:54804507-54898271
            chr12:5928665-5930039

2. Open Comp Plot and load the regions with
   - **File -> Load Region File**
3. Only display cnvs from the file used to make the calls.
4. Compute the median log R ratio for the first region and view the results in Custom Plot
   - **Actions -> Median LRR -> Compute**
     - This will create the directory **[ProjectDir]/medianLRR/**
   - When the computation has finished, click the **Custom Plot** button
   - This will plot each sample’s median LRR and MAD (median absolute difference) LRR for the region.

  #### NOTE:

            If MEDIAN is not on the x-axis and MAD is not on the y-axis, use the expandable menu on the left side of the plot.  The first option chosen will be plotted on the x-axis and the second on the y-axis.

   ![Image of a plot of median LRR vs median absolute difference with three distinct clusters and the copy number 2 cluster is off center from zero](/Images/cnv_interpretation_1.png)

   - We want to see a plot like this with clear clusters for copy number 2, heterozygous deletion, and homozygous deletion. Note that CN2 is not centered on 0.0 in this example. We can attempt to correct this in the steps below.

![Image of a plot of median LRR vs median absolute difference with one noisy cluster](/Images/cnv_interpretation_2.png)

   - This example has an EMP2 of 0.0008, but there is no clear separation in the data. This is a false positive.
  
  #### NOTE:

            In Custom Plot, the most useful color code options are Heat Map and the option named after the CNV file.

5. Back in Comp Plot, select one of the colored bars -> **To Trailer -> Selected**
6. In Trailer, **Actions -> To ScatterPlot**
7. On marker plots that are marked unknown, use heat map to identify clusters

![Image of Scatter Plot showing the heatmap view of a marker with user drawn boxes around genotype clusters](/Images/cnv_interpretation_3.png)

8. Examine the Hardy-Weinberg value for each marker
   - Hardy-Weinberg is non-significant if percentages are 0.25, 0.5, 0.25 for AA, AB, BB.  Significance usually indicates noise, measurement error, or biased data (however, sickle cell is a scenario where significant deviation from HW is biologically real).

9. Manually modify clusters for a marker until Hardy-Weinberg becomes non-significant. Set clusters to AA (x-axis), AB, or BB (y-axis).

![Image of Scatter Plot showing the Genotype view of a marker with user drawn boxes around genotype clusters](/Images/cnv_interpretation_4.png)

10. Close **Scatterplot > New cluster filters have been created. Would you like to append them to the permanent file? > Yes, overwrite**
11. Return to Comp Plot and repeat **Median LRR**, but with **Recompute LRR** checked
12. Custom Plot should now show the CN2 cluster centered around 0.0

![Image of a plot of median LRR vs median absolute difference with three distinct clusters and the copy number 2 cluster is centered at zero](/Images/cnv_interpretation_5.png)

13. In **[ProjectDir]/medianLRR/**, there will be a file named **LRR\_MEDIAN\_chr#\_#-#\_RECOMPUTE\_LRR\_ARTIFICIAL.xln**.  
    - Append affliction status to this file, then conduct a linear regression between AFF and CN types.  
    - The **ADJ\_MEDIAN\_chr#:#-#** column corresponds to the x-axis in Custom Plot.  In the example, we declare everything less than -0.2 a homozygous deletion based on the visualization.

14. Repeat steps 4 to 13 for each additional signficiant region.

15. Recall CNVs
    - Add false positive regions to the problematic regions file for the relevant genome build
      - Eg. [.genvisis/resources/Genome/hg38/problematicRegions_hg38.dat](../#/documentation/resources-directory)
    - In the main Genvisis window, run **Tools > Compute custom centroids file**
      - This creates **data/custom.cent**
    - Call and filter CNVs a second time. The custom centroids file and updated problematic regions file should remove the false positive calls and correctly center the true positives.
