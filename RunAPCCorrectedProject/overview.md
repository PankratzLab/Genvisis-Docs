## Overview

Running a PC-corrected project is an option only after you have already run a project in Genvisis. The PC-corrected project is a copy of the original project in which X and Y are transformed based on the nearest genotype cluster using a user-specified number of principal components. Genvisis recomputes LRR and BAF on the new X and Y values.

### Creates files:
* data/
  * batch.txt (if present in the parent project)
  * import.ser
  * linker.txt
  * markerdetails.ser
  * markers.ser
  * pedigree.txt
  * SampleData.txt
    * DNA
    * Batch (if a batch file was used)
    * CLASS=Batch (if a batch file was used)
    * CLASS=Sex
    * CLASS=Estimated Sex;0=Unknown;1=Male;2=Female;3=Klinefelter;4=UPD Klinefelter;5=Mosaic Klinefelter;6=Triple X;7=Mosaic Triple X;8=Turner;9=Mosaic Turner
    * Class=ImputedRace;1=White;2=African American;3=Hispanic;4=Asian
    * % African
    * % Asian
    * % European
    * mzTwinID
    * Aneuploidy
    * AnyTrisomy
    * AnyLargeMosaicEvent
    * numChrsWithEventGreaterThan4
    * NumberMosaicEventsDetected
    * ProportionGenomeMosaic
    * PCA/PCA\_GENVISIS/PCA\_GENVISISLRR\_SD
    * PCA/PCA\_GENVISIS/PCA\_GENVISISGenotype\_callrate
    * PCA/PCA\_GENVISIS/PCA\_GENVISISCLASS=Exclude
  * samples.ser
* samples/
    * Empty. The first step of the PC-Corrected workflow Transpose Marker Files to Samples Files will populate this directory.
* scripts/
    * .slrm file
  * .toml file
  * Appears if Create script with steps to process corrected data and call CNVs? option is checked in the Create PC-Corrected Project step.
* transposed/
    * Marker dominant .mdRAF files with recalculated X, Y, LRR, and BAF values.
* #\_markersThatFailedCorrection.txt
    * List of markers that could not be PC-corrected
* AB\_lookup\_parsed.dat
* .csv manifest (Illumina projects only)
* markerPositions.txt
