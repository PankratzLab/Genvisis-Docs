## Process Affymetrix CEL Files 

#### 1: Create Marker Positions step [affy-markers] must have been run already or must be selected

#### 2: Directory with Affymetrix Power Tools executables (should contain apt-probset-genotype, etc.)
These files begin with **apt-**, such as **apt-probeset-genotype**.

#### 3: Directory with Affymetrix Power Tools library files (should contain GenomeWideSNP\_6.cdf, etc.)
These files begin with **GenomeWideSNP\_6**, such as **GenomeWideSNP\_6.cdf**.

#### 4: A target sketch file (such as hapmap.quant-norm.normalization-target.txt)
This comes with Affymetrix Power Tools.

#### 5: (optional) Use the full Affymetrix cdf, which contains more mitochondrial probesets
This option may be of interest if you are examining mitochondrial DNA copy number.

#### 6: (optional) Sample name override file containing the following two columns: CurrentID, DesiredID
Samples will be named after their **.CEL*** file.  For example, NA12878.CEL will be named NA12878 in Genvisis files such as **SampleData.txt**.  To give samples different names than their **.CEL** files, supply a text file with two columns and no header.  In the first column place the current sample name and in the second column place the new name.

#### 7: Number of threads
Genvisis can process **.CEL** files in parallel. More threads will result in the job finishing faster, but requires more
memory usage.
