# Interpret CNV Analysis Results

1. Create a list of significant regions using the first and last SNPs on a chr that are EMP2 < 0.05. For example:

       chr7:31550705-31552108
       chr10:18550421-18572274
       chr11:54804507-54898271
       chr12:5928665-5930039

2. Open CompPlot and load the regions with
    1. **File -> Load Region File**
3. Only display cnvs from the file used to make the calls.
4. Compute the median log R ratio for the region and view the results in 2D Plot
   1. **Actions -> Median LRR -> Compute -> 2D Plot**
   2. This will plot each sample’s median LRR and MAD (median absolute difference) LRR for the region.
   3. Note: If MEDIAN is not on the x-axis and MAD is not on the y-axis, use the expandable menu on the left side of the plot.  The first option chosen will be plotted on the x-axis and the second on the y-axis.
