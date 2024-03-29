## Create Marker Positions
This step uses an Illumina manifest file to determine where probes lie in the genome.

#### 1: An Illumina Manifest file
Choose the [.csv version of the manifest](../#/documentation/AppendixAGenomeStudio--finding-illumina-manifest-files) used to create the original project in GenomeStudio. This file should already be saved in the project directory.

#### 2: (optional) Perform LiftOver to lift manifest positions to project build
Check this option if your manifest is in a different genome build than the Genvisis project (e.g., if the manifest is hg37 but Genvisis was set to hg38 during project creation).
