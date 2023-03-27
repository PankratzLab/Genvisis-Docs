### Create Marker Positions (Illumina)

This step uses an Illumina manifest file to determine where probes lie in the genome.

Choose the [.csv version of the manifest](https://docs.google.com/document/d/1BMu1zp8er9NY-QFRh-7ZOeX1HnGj_yAYYh3BarASwPY/edit?pli=1#bookmark=id.e14mve4bgxmr) used to create the original project in GenomeStudio. This file should already be in **[ProjectDir]**.

If your manifest is in a different GenomeBuild than the Genvisis project (eg. manifest is **hg37 **and Genvisis was set to **hg38 **during project creation), choose the option **Perform LiftOver to lift manifest positions to project build**.
