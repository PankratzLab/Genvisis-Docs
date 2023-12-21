## Run Marker BLAST Annotation

[BLAST (Basic Local Alignment Search Tool)](https://blast.ncbi.nlm.nih.gov/Blast.cgi) (external link) determines if markers are useful by aligning the probe sequences to the genome. A marker is not useful if it aligns to multiple locations on a genome.

BLAST will run on the marker positions in [markerPositions.txt](../#/documentation/RunTheGenvisisWorkflow--create-marker-positions-illumina).

#### 1: Parse Sample Files step [parse-samples] must have been run already or must be selected
This step uses the sampRAF files that were created in the Parse Sample Files step.

#### 2: Word size (length of the smallest continuous match reported)
[1-100, default 40]
A smaller value lengthens the runtime
Markers are 50 bp in length
Checks if subunits of the marker have matches in the sample genome?

#### 3: Full path to an Illumina manifest file (e.g., HumanExome-12-v1-o-B.csv)
You must provide a manifest with probe sequences.

#### 4: (optional) Marker positions file to override MarkerSet positions with (e.g. for a different genome build) (e.g. markerPositions.txt)
Use this option if you want to BLAST on a different genome build than that of your project. For example, if the project was created in hg37 and the positions in *markerPositions.txt* are hg37, you can provide an alternative markerPositions file with positions in hg38 for this part.

#### 5: Number of threads

#### 6: Download remotely available BLAST program requirement
Genvisis is built to work with BLAST 2.13.0 and will automatically download it if it is not available in your local environment.
