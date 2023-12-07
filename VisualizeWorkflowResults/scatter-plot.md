# ScatterPlot

ScatterPlot displays data for all individuals for a single marker and allows you to annotate and triage markers. For instance, those markers failing a QC metric such as call rate or Hardy-Weinberg equilibrium can be reviewed to see if they could be manually reclustered to rescue the marker. In addition, you can explore and correct batch effects, rescuing many markers with lower-quality data.

Samples are plotted in scatter plot format with one plot per marker.

You can zoom in and out with the scroll wheel of a mouse. Move a zoomed in plot around by holding down right click (Windows) or control-click (Mac).

Point colors change between autosomal and sex chromosomes for quick identification when scrolling through large numbers of markers. For autosomes, AA is dark blue, AB is red, and BB is purple. On sex chromosomes, AA is green, AB is light blue, and BB is indigo.

Marker lists can be created, loaded, edited, and deleted under File.

When you first open ScatterPlot, Genvisis will generate the file **data/exampleScatterPlotMarkers.txt** with the first 10 markers in order to have something to display.

On the right hand side, under **View Controls**, the option **Display Mendelian Errors** will draw lines between samples that have Mendelian errors. Blue is used for mother-offspring and green for father-offspring errors.

In the upper right hand corner of the screen is a window with four tabs: **Control**, **Centroid**, **GC Adjust**, and **Annotation**.

In the **Annotation** tab, you can enter a description in the “enter new annotation here” box. It will then be entered into the list of existing annotations with the first letter of the annotation now available as a hotkey, e.g., Monomorphic and Extra heterozygote clusters are default annotations. When viewing a marker, if you hit ‘m’ or ‘e’, the marker will be flagged for that annotation and you’ll automatically move to the next marker. In this way, you can very quickly move through markers, hitting only the annotation shortcuts on the keyboard.

High-quality markers have tight clusters with A/A on the X-axis, B/B on the Y-axis, and A/B in the middle of the plot.

Once Marker BLAST Annotation has been run, the **BLAST Metrics** tab in the lower right hand corner of the window will include data about the marker. This Includes the metrics **Has Perfect Match?**, **# Off-Target Alignments**, and **# On-Target (mismatched) Alignments (>80.0% match)**.
1. Click the button **Show BLAST Results** to load the **BlastViewer**
- The first row in the viewer is the probe sequence that Illumina reported and what nucleotides the A and B alleles are
- The subsequent rows are the results of the BLAST and what locations the sequence is matching to
- When examining off target matches, look at what allele is present. For example, if the off target match has the B allele, the values in the scatterplot will be above the x-axis, which represents the A allele.
- If the off target matches are a mixture of both alleles (multiple off target matches), the data will be offset from both axes
- Complementary nucleotides can appear as alleles in off target matches since they share the same fluorescent tag as the known allele. For example, C is the alternate allele and an off target match lists G as the allele.
2. In the Scatter Plot window, click **File -> New Marker List**. This produces a pop up window where you can paste marker IDs and limit the scatterplots shown to just those instead of thousands. The list of IDs must be saved to a dir with **File name (full path):** in order to use them.
To add markers to an existing list, use **File -> Edit Existing Marker List**
