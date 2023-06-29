# GenomeStudio Background

Illumina Beadchip technology uses a probe 50 bp in length and assesses the variant after the 50th bp. AT nucleotides are tagged with a red fluorescent dye and GC nucleotides with green. Samples are fluoresced and the light intensity is measured.  Measurements are plotted such that the x-axis is a measure of red intensity, and a pure red signal is labeled the A probe. The y-axis measures green intensity and is called the B probe. Measurements in the middle of the graph cluster as a yellow mixture.  Twelve samples per chip can be run at a time.

The SNP Graph in GenomeStudio represents the x and y light intensity values transformed to R and Theta.  R is the total intensity, or x + y. Theta is the angle of a value on the x-axis. The three clusters on the SNP Graph are the AA, AB, and BB alleles for the SNP. The R-value divided by the centroid of a data cluster is a normalized value called Log R Ratio, which is mapped in Trailer Plot of Genvisis.
