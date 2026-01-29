## Create Marker Positions

This step uses an Affymetrix manifest file to determine where probes lie in the genome.

#### 1: An Affymetrix Annotation file
The annotation file **.genvisis/resources/Arrays/AffySnp6/GenomeWideSNP\_6.na35.annot.csv** will automatically load from the pre-existing Genvisis [resources directory](../#/documentation/resources-directory). This file uses an hg19 array.

#### 2.1: (optional) Perform LiftOver to lift annotation positions to project build
This option will convert marker positions in the annotation file to the genome build Genvisis was set to at project creation. For example, if a project was set to hg38 and the annotation file is in hg19, the marker positions will be converted to hg38.

This option is automatically set to true.

#### 2.2: Genome Build of the specified annotation file
Select the appropriate genome build of your annotation file. The default is hg19.
