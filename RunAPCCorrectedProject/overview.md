## Overview

A PC-corrected project is a copy of your original Genvisis project in which X and Y are transformed based on the nearest genotype cluster using a user-specified number of principal components. Genvisis recomputes LRR and BAF on the new X and Y values. You cannot run a PC-corrected project without first running a project in Genvisis.

When you run a PC-corrected project, Genvisis creates several files:

- data/
    - batch.txt (if present in the parent project)
    - import.ser
    - linker.txt
    - markerdetails.ser
    - markers.ser
    - pedigree.txt
    - SampleData.txt
        - DNA
        - Batch (if a batch file was used)
        - CLASS=Batch (if a batch file was used)
        - CLASS=Sex
        - CLASS=Estimated Sex;0=Unknown;1=Male;2=Female;3=Klinefelter;4=UPD Klinefelter;5=Mosaic Klinefelter;6=Triple X;7=Mosaic Triple X;8=Turner;9=Mosaic Turner
        - Class=ImputedRace;1=White;2=African American;3=Hispanic;4=Asian
        - % African
        - % Asian
        - % European
        - mzTwinID
        - Aneuploidy
        - AnyTrisomy
        - AnyLargeMosaicEvent
        - numChrsWithEventGreaterThan4
        - NumberMosaicEventsDetected
        - ProportionGenomeMosaic
        - PCA/PCA\_GENVISIS/PCA\_GENVISISLRR\_SD
        - PCA/PCA\_GENVISIS/PCA\_GENVISISGenotype\_callrate
        - PCA/PCA\_GENVISIS/PCA\_GENVISISCLASS=Exclude
    - samples.ser
- samples/
    - Initially this directory will be empty; the first step of the PC-Corrected workflow (**Transpose Marker Files to Samples Files**) will populate this directory
- scripts/
    - .slrm file
    - .toml file
    - Appears if **Create PC-Corrected Project step > Create script with steps to process corrected data and call CNVs?** is checked
- transposed/
    - marker-dominant **.mdRAF** files with recalculated X, Y, LRR, and BAF values
- #\_markersThatFailedCorrection.txt
    - List of markers that could not be PC-corrected
- AB\_lookup\_parsed.dat
- **.csv** manifest (Illumina projects only)
- **markerPositions.txt**
