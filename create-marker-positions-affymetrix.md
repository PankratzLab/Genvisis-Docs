## Create Marker Positions (Affymetrix)

#### 1: An Affymetrix Manifest file
This step uses an Affymetrix manifest file to determine where probes lie in the genome.

**.genvisis/resources/Arrays/AffySnp6/GenomeWideSNP_6.na35.annot.csv** will automatically load from the pre-existing Genvisis resources. This file uses an hg19 array.

Choose the [.csv version of the manifest](https://docs.google.com/document/d/1BMu1zp8er9NY-QFRh-7ZOeX1HnGj_yAYYh3BarASwPY/edit?pli=1#bookmark=id.e14mve4bgxmr) used to create the original project in GenomeStudio. This file should already be saved in the project directory.

#### 2.1: (optional) Perform LiftOver to lift manifest positions to project build
Check this option if your manifest is in a different GenomeBuild than the Genvisis project (e.g., if the manifest is **hg37** but Genvisis was set to **hg38** during project creation).

#### 2.2: Genome Build of the specified manifest file
Select the appropriate genome build of your manifest file. Select **HG19** in option 2.2 if using **GenomeWideSNP_6.na35.annot.csv**.
