# Affymetrix Workflow Output

### 1. Create Marker Positions
- **markerPositions.txt**
- **GenomeWideSNP_6.na35.annot.rsLookup.txt**

### 2. Process Affymetrix CEL Files
- **[ProjectDir]/transposed**
  - Contains .mdRAF files, which are marker dominant files.
- **transposed/outliers.ser**
  - The outlier file tends to be small for Illumina data sets, but Affymetrix projects have much larger values on average. This can increase the number of outliers in a dataset and make it such that outliers.ser becomes inefficient and no longer leads to the compression it was designed to achieve. In those cases, Genvisis uses a linear scaling factor (e.g., divide all values by 100) to force nearly all values to be less than 32. 
  - If Genvisis detects that the default scale factor of 1.0 is not sufficient (too many outliers are being found), then Parse Samples (Illumina projects) or Process Affymetrix CEL Files (Affymetrix projects) will automatically restart with a larger scaling factor.
- See [Transpose Data into Marker-Dominant Files](../#/documentation/WorkflowOutput--output-illumina) for a detailed explanation of the .mdRAF files.

### 3. Transpose Marker Files to Sample Files
- **[ProjectDir]/samples**
- **[ProjectDir]/ListOfMarkers.txt**
- **[ProjectDir]/ListOfSamples.txt**
- **data/markers.ser**
- **data/samples.ser**
- **samples/outliers.ser**

### 4. Run Marker BLAST Annotation
- **[ProjectDir]/Blasts**
  - Contains a zipped file for every thread used.
- **[ProjectDir]/data/blast.vcf.gz**
- **[ProjectDir]/data/blast.vcf.gz.tbi**
  - An index of blast.vcf.gz
- See [Run Market BLAST Annotation](../#/documentation/WorkflowOutput--output-illumina) for a detailed explanation of the BLAST files.
