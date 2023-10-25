# Trailer Plot

Trailer displays data for all markers for one individual and allows you to differentiate between good and bad copy number variant (CNV) calls, overlay the results from different CNV callers, and visualize different transformations of the data (e.g., GC correction). You can also interrogate aneuploidies, large mosaic events, and contamination and sample quality.

This will load all of the markers for one individual and orient them based on genomic position separated by chromosome. The first plot that loads is the first chromosome of the first sample. In the center will be the sample ID, a blank text box with left and right arrows that is not relevant unless using a region list file, and a text box with right and left arrows identifying the chromosome and the base pairs visible (eg. chr1:1-249,218,902). If you zoom in, the base pairs listed will change to reflect what is present on screen.

Two plots are visible: Log R Ratio and B Allele Frequency. Both plots will have a gap where there is no data due to the chromosome’s centromere. The center of the Log R Ratio plot is a gray line that is equal to 0. A Log R Ratio of 0 implies a copy number of 2, or a normal copy number (a population normalized average of 0). Markers don’t fall perfectly on the line, but in a normal diploid genotype, we will see a tight standard deviation around 0. Conversely, markers significantly below 0 indicate a deletion and significantly above indicate a duplication. An individual marker can be noisy, so we look for numerous markers in a row before believing there is a deletion or duplication. A SD of 0.1 is good, 0.25 is borderline acceptable, 0.32 to 0.5 is sample failure, and above 0.5 is bad.

Red points are heterozygous calls and black points are homozygous. 

The B Allele Frequency plot shows if there are 0, 1, or 2 copies of the B allele. This is presented as a frequency, or 0, 0.5, or 1. Only those 3 bands are expected in a diploid genotype (AA, AB, or BB). An individual with a deletion will only have a marker at 0 or 1 (either only one B allele or only one A allele). A duplication will appear as 0, 0.33, 0.66, or 1 (AAA, AAB, ABB, or BBB). If more than 4 bands appear, this is probably due to contamination. Two samples mixed together would lead to 4 alleles at each locus, or 5 bands at 0, 0.25, 0.5, 0.75, and 1. More than 5 bands means contamination from more than 2 samples. A weird CNV can cause multiple banding, but if you see the same number of bands genome wide, then it’s contamination.

We’re not interested in markers near 0 or 1 on the BAF plot, but in between the two. Anything between 0.15 and 0.85 is considered a heterozygous call.

The BAF and LRR plots should be read in conjunction with each other. If the BAF plot has only two bands at 0 and 1 and the LRR plot shows markers below the median at that location, it’s a deletion. If the LRR plot is centered at the median instead, this is more likely a run of homozygosity and an indication that the subject’s parents were closely related, such as cousins. If the BAF plot shows a split pattern, but the two bands aren’t near 0.33 and 0.66, this can be a mosaic duplication, deletion, or uniparental disomy (UPD), where the subject inherited two chromosomes from the same parent. The alteration is UPD if the median LRR is centered on the line, and mosaic duplication or deletion if above or below. The more cells that have the alteration, the further the two BAF bands will be apart and the easier it will be to tell if the LRR markers are above, on, or below the median line.

1. **File** -> **New Region List File**
2. A pop up window appears named:
- **Sample IDs with (optional) UCSC regions and comments (tab-separated, one set per line):**
- For example:
  - 202030300404	chr1:55-345	Signs of contamination
3. If a UCSC is not provided, Genvisis assumes you are looking at chr1. It is the largest chromosome and usually representative of the rest.
4. Under **File name (full path):** is a text field with a … button. You need to provide a location to save the region list file.
5. Click **Create**. The text field in the center of the screen that was blank (and is above the field identifying the chromosome and base pairs visible) will now be populated with index numbers for the region list, e.g. 1 of 24.
6. **Show QC** option on the trailer plot toolbar has 3 options:
Hide QC
Genome
Region
7. Choosing Genome or Region will display stats between the two text fields. If you select region, zooming will change the stats as they are for the region visible on the plot.
8. Colors option on the trailer plot toolbar has 3 options:
Default
GC content
custom
9. For GC content, blue is lower GC content and red is higher. Regions with a high GC content have a low intensity on average.
10. If a Log R Ratio plot is wavy, color code it by GC content. If the peaks and values correspond to GC content, you can clean this up with the **Adjustments** option on the toolbar:
- Adjust by GC content
- Adjust with gc parameter file
11. Adjust by GC content will smooth out a wavy plot if that was the issue.

	To add Marker Stats to the Trailer Plot, run:

        java -jar ~/genvisis.jar org.genvisis.cnv.analysis.MarkerStats proj=~/[path to .properties file for project] out=marker_lrr_sd.xln
