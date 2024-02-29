## Run Marker BLAST Annotation

[BLAST (Basic Local Alignment Search Tool)](https://blast.ncbi.nlm.nih.gov/Blast.cgi) (external link) is used to determine if markers are problematic by aligning the probe sequences to the genome. A marker is likely problematic if it aligns to multiple locations on a genome. BLAST will run on the marker positions in [markerPositions.txt](../#/documentation/RunTheGenvisisWorkflow--create-marker-positions-illumina).

If you do not have a [probe sequence file](../#/documentation/GetStarted--find-required-raw-data-files), Genvisis cannot run the Run Marker BLAST Annotation step. Verify that Run Marker BLAST Annotation is unchecked in the Genvisis workflow. If Genvisis does not run the Run Marker BLAST Annotation step, it will automatically identify markers that are likely to be problematic based on mappability (which uses the reference genome instead of probe sequences to identify regions of the genome that appear multiple times and thus may be problematic).

BLAST is superior to mappability. If a probe set file is available, we recommend running Run Marker BLAST Annotation rather than relying on mappability.

#### 1: Parse Sample Files step [parse-samples] must have been run already or must be selected
This step uses the sampRAF files that were created in the [Parse Samples Files](../#/documentation/RunTheGenvisisWorkflow--parse-sample-files-illumina) step.

#### 2: Word size (length of the smallest continuous match reported)
[1-100, default 40]
A smaller value lengthens the runtime
Markers are 50 bp in length
Checks if subunits of the marker have matches in the sample genome?

#### 3: Full path to an Illumina manifest file (e.g., HumanExome-12-v1-o-B.csv)
You must provide a manifest with probe sequences. Contact Illumina if you need assistance locating a manifest file that contains probe sequences.

#### 4: (optional) Marker positions file to override MarkerSet positions with (e.g. for a different genome build) (e.g. markerPositions.txt)
Use this option if you want to BLAST on a different genome build than that of your project. For example, if the project was created in hg37 and the positions in *markerPositions.txt* are hg37, you can provide an alternative markerPositions file with positions in hg38 for this part.

#### 5: Number of threads

#### 6: Download remotely available BLAST program requirement
Genvisis is built to work with BLAST 2.13.0 and will automatically download it if it is not available in your local environment.
