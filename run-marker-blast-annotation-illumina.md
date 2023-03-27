### Run Marker BLAST Annotation (Illumina)

BLAST (Basic Local Alignment Search Tool) aligns probe sequence to the genome. This determines if markers are useful or not, not useful being if a marker aligns to multiple locations on a genome.

You must provide a manifest with probe sequences

BLAST will run on the marker positions in markerPositions.txt.

Part 3 of this step (optional): If you want to BLAST on a different genome build than that of your project, use **Marker positions file to override MarkerSet positions with**. For example, if the project was created in hg37 and the positions in markerPositions.txt are hg37, you can provide an alternative markerPositions file with positions in **hg38** for this part.
