## Run Marker BLAST Annotation

[BLAST (Basic Local Alignment Search Tool)](https://blast.ncbi.nlm.nih.gov/Blast.cgi) determines if markers are useful by aligning the probe sequences to the genome. A marker is not useful if it aligns to multiple locations on a genome.

BLAST will run on the marker positions in [markerPositions.txt](../#/documentation/RunTheGenvisisWorkflow--create-marker-positions-affymetrix).

#### 1: Transpose Marker Files to Samples Files step [reverse-transpose] must have been run already or must be selected

#### 2: Word size (length of the smallest continuous match reported)

The default is 20 since Affymetrix probes are 25bp in size.

#### 3: An Affymetrix Probe Set file
A file of probe sequences. The default file, **GenomeWideSNP\_6.probe\_tab**, can be found inside Affymetrix Power Tools in the directory **/CD_GenomeWideSNP_6_rev3/Full/GenomeWideSNP_6/LibFiles/**.

#### 4: An Affymetrix Annotation file
The default file is **.genvisis/resources/Arrays/AffySnp6/GenomeWideSNP_6.na35.annot.csv**.

#### 5: (optional) Marker positions file to override MarkerSet positions with (e.g. for a different genome build) (e.g. markerPositions.txt)
Use this option if you want to BLAST on a different genome build than that of your project. For example, if the project was created in hg37 and the positions in markerPositions.txt are hg37, you can provide an alternative markerPositions file with positions in **hg38** for this part.

#### 6: Number of threads

Genvisis can BLAST multiple samples in parallel. More threads will result in the job finishing faster, but requires more memory usage.

#### 7: Use locally available BLAST program requirement

Genvisis is built to work with BLAST 2.13.0 and will automatically download it if it is not available in your local environment.
