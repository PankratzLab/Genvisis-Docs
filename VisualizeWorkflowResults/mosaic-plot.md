# Mosaic Plot

MosaicPlot visualizes all chromosomal arms for all samples at once. The outliers (the colored dots) indicate chromosomal arms where a subset of their cells (such a mixture is called a mosaic) have been deleted or duplicated or have evidence of uniparental disomy. These mCAs may increase the risk of disease, especially cancer, and may also cause genotyping errors.

1. When you place your cursor over a point, the point turns red and all the points that are chromosomes for the same individual turn yellow.
2. **File -> Hide Excluded** will remove samples previously marked as excluded from the plot
3. You can sort by chromosome in **Mosaicism.xln**, delete problematic chromosomes, and reload the Mosaic Plot to see it without them included (make a copy of **Mosaicism.xln** before deleting rows).
4. Clicking a point will bring up the sample id, chromosome, and chromosome arm. Clicking on this tag will open [Trailer Plot](../#/documentation/VisualizeWorkflowResults--trailer-plot).
- In the B allele frequency plot, if there are four bands instead of the normal three, the farther apart the center two bands are, the higher the percentage of cells that have the mosaicism event.
- On the Trailer Plot toolbar, **CNV Calls -> Call Mosaicism** will place a red bar parallel to the Log R Ratio and the B Allele Frequency plots where Genvisis calculated mosaicism to be.
- Putting the cursor over the red bar will show the start and stop position, length, and estimate score.
- **CNV Calls -> Quantify Mosaicism** - force call region.
5. Whenever you click on a point, its id and chromosome arm are copied to the clipboard
- These can be pasted into a text file and columns added for color coding points
- For example	

        rs2452345 chr19p 1 likely duplication
		rs4563456 chr19q 1 likely duplication
		rs6765550 chr15q 2 deletion of whole chromosome

- The integers 1 and 2 correspond to colors and are in a third column. The fourth column is for comments.
- 1 = black; 2 = blue; 3 = purple; 4 = green; 5 = red; 6 = brown
- Name the file **mosaic_colors.txt** and place it in **[ProjectDir]/data** and the mosaic plot will automatically color points.
