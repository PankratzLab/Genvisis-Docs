## Transpose Data Into Marker-Dominant Files

The **.sampRAF** files created previously (in [Parse Samples Files](../#/documentation/RunTheGenvisisWorkflow--parse-sample-files-illumina)) contain one sample per file. This step creates a copy of the data but with one marker per file, which allows the same marker to be examined for each sample without iterating through every sampRAF.

#### 1: Parse Sample Files step [parse-samples] must have been run already or must be selected
This step uses the sampRAF files that were created in the [Parse Samples Files](../#/documentation/RunTheGenvisisWorkflow--parse-sample-files-illumina) step.
