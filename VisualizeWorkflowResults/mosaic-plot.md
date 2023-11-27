# MosaicPlot

MosaicPlot visualizes all chromosomal arms for all samples at once. The outliers (colored dots) indicate chromosomal arms in which a subset of their cells (i.e., a mosaic) have been deleted or duplicated or have evidence of uniparental disomy. These mosaic chromosomal alterations (mCAs) may increase the risk of disease, especially cancer, and may cause genotyping errors.

When you place your cursor over a point, the point turns red and all of the points represent chromosomes for that same individual turn yellow.

**File -> Hide Excluded** will remove samples previously marked as excluded from the plot.

You may wish to remove probematic chromosomes from your plot. To do so, make a copy of **Mosaicism.xln**, sort by chromosome, delete the problematic chromosomes, and then reload your plot.

Clicking on a point will bring up the sample ID, chromosome, and chromosomal arm. Clicking on this tag will open [Trailer Plot](../#/documentation/VisualizeWorkflowResults--trailer-plot).
- In the B allele frequency plot, if there are four bands instead of the typical three, the distance between the two center bands indicates the percentage of cells that have this mosaicism event (a greater distance between the two center bands means a higher percentage of cells that have this mosaicism event).
- On the TrailerPlot toolbar, **CNV Calls -> Call Mosaicism** will place a red bar parallel to the Log R Ratio and the B Allele Frequency plots in locations determined by Genvisis to be mosaic.
- Putting the cursor over the red bar will show the start and stop position, length, and estimate score.
- **CNV Calls -> Quantify Mosaicism** - force call region.

Whenever you click on a point, its ID and chromosomal arm are copied to the clipboard.
- These can be pasted into a text file and columns added for color coding points.
- For example	
        rs2452345 chr19p 1 likely duplication
		rs4563456 chr19q 1 likely duplication
		rs6765550 chr15q 2 deletion of whole chromosome

- The integers 1 and 2 correspond to colors and are in a third column. The fourth column is for comments.
- 1 = black; 2 = blue; 3 = purple; 4 = green; 5 = red; 6 = brown
- Name the file **mosaic_colors.txt** and place it in **[ProjectDir]/data** and the mosaic plot will automatically color points.
