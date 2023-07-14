## Parse Sample Files
This step converts the .csv report files into a native format for Genvisis.

#### 1: Create Marker Positions step [illumina-markers] must have been run already or must be selected
This step uses the file created in Create Marker Positions.

#### 2: (optional) Sample name override file containing the following two columns: CurrentID, DesiredID
Use this option to change the IDs from those IDs in your report files. For example, if your report files contain the sentrix IDs, you can use this option to convert these to the study IDs in the sampRAF files.

#### 3: (optional) Interrupt parsing if a sample doesn't contain all expected markers

#### 4: Number of threads
Genvisis can parse sample files in parallel. More threads will result in the job finishing faster, but requires more
memory usage.
