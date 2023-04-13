## Process Affymetrix CEL Files 

#### 1: Create Marker Positions step [affy-markers] must have been run already or must be selected

#### 2: Directory with Affy Power Tools executables (should contain apt-probset-genotype, etc. Available at http://www.affymetrix.com/)
These files begin with **apt-**, such as **apt-probeset-genotype**.

#### 3: Directory with Affy Power Tools library files (should contain GenomeWideSNP_6.cdf, etc. Available at http://www.affymetrix.com/)
These files begin with **GenomeWideSNP_6**, such as **GenomeWideSNP_6.cdf**.

#### 4: A target sketch file (such as hapmap.quant-norm.normalization-target.txt)

#### 5: (optional) Use the full affymetrix cdf, which contains more mitochondrial probesets
This option may be of interest if you are examining mitochondrial DNA copy number.

#### 6: (optional) Sample name override file containing the following two columns: CurrentID, DesiredID

#### 7: Number of threads
