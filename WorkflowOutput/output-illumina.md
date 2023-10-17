# Illumina Workflow Output

### 1. Create Marker Positions
- **[ProjectDir]/markerPositions.txt**
  - This text file contains the name of the probe, the chromosome that the probe is on, and the position of the probe in the chromosome. Probes with chromosome and position set to 0 are considered no longer useful by the supplier of the probes.
- Probe names are usually rsID, but can also have GSA-rsID from the GSA array, exmid from Exome Chip content, or #:#.

### 2. Parse Sample Files
- **[ProjectDir]/samples**
  - Contains **.sampRAF**, which are sample dominant files.
- **[ProjectDir]/ListOfMarkers.txt**
- **[ProjectDir]/ListOfSamples.txt**
- **data/markers.ser**
  - **markers.ser** contains the Marker Detail Set, or information about all markers in the project (eg. what chromosome the marker is on; what position the marker is at). No marker details are contained in the .sampRAF files; only marker data unique to each sample is present.
  - The markers in the .sampRAF files and markers.ser are in the same order, which allows marker details to be paired with the markers of a sample. If a .sampRAF file or the markers.ser file is modified, its checksum will change, and the files will have to be recreated as the order of markers in each file can no longer be assumed.
- **data/samples.ser**
- **samples/outliers.ser**
  - The .sampRAF and .mdRAF files are compressed using half-precision floats; values are limited to the range -32 to 32. This leads to a loss of precision at the fourth decimal place, but this doesn't have a meaningful effect on Genvisis analyses. In most Illumina data sets, the X and Y values tend to be in the range 0 to 3. Any values outside of the -32 to 32 range are stored in outliers.ser with only a dummy placeholder where that value would have resided in the .sampRAF and .mdRAF files.
  - A hashtable containing the same outlier values is also present at the end of each .sampRAF and .mdRAF file, which allows outliers.ser to be recreated if it ever gets deleted.

### 3. Run Marker BLAST Annotation
- **[ProjectDir]/Blasts**
  - Contains a zipped file for every thread used.
- **[ProjectDir]/data/blast.vcf.gz**
- **[ProjectDir]/data/blast.vcf.gz.tbi**
  - An index of blast.vcf.gz
- Data in the blast.vcf file can be used to judge the quality of a particular marker.
- **blast.vcf**.gz contains eight columns:
  - CHROM - chromosome number
  - POS - position
  - ID - marker ID
  - REF - reference allele
  - ALT - alternate allele
  - QUAL - quality information
  - FILTER - filter information
  - INFO
    - ALIGNMENT_HISTOGRAM=#
      - Number of alignments
    - BLAST_EVALUE_COUNTS=#
      - The confidence BLAST has that it got the right location
    - MARKER_GC_CONTENT=#
      - The percentage of the 50 base pairs that are a G or a C
      - 0.42 is the average across the genome
      - An A binds with a T using two hydrogen bonds, whereas a G binds with a C using three hydrogen bonds. So a region with a higher GC content will lead to tighter bonds and require more energy to break apart. This will affect the amount of DNA that binds to the probe and alter the intensity values that Genvisis uses to call copy number variation.
    - OFF_T_ALIGNMENTS=#
      - Number of off target alignments that are different from what the manifest reported.
    - ON_T_ALIGNMENTS_NON_PERFECT
      - Number of alignments that are are less than 50 perfect matches (e.g., 49 matches and one mismatch).
    - PERFECT_MATCH
      - Lists number of base pairs matched, chromosome matched on, and the position on the chromosome matched
- A perfect match of 50 for a probe is ideal. If all 50 base pairs match, that indicates that the probe will hybridize to this region of the genome.
- If the probe sequence matches to multiple locations in the genome or to no locations, then those markers will be set to chr0.
- The reference and alternate alleles are usually a single nucleotide each. For the chr0 markers, REF may be set to N and ALT set to two nucleotides if BLAST can’t identify the appropriate reference allele.
- To quickly identify the percentage of high quality matches, divide the number of high quality lines by the total number of lines.
  - Linux example:

        /# Number of lines where Off Target and Non-Perfect alignments are null and there is a # perfect match of 50:
        zcat blast.vcf.gz | grep “OFF_T_ALIGNMENTS=\.” | grep “ON_T_ALIGNMENTS_NON_PERFECT=\.” | grep “PERFECT_MATCH=50” | wc -l

        /# Total number of lines in the file:
        zcat blast.vcf.gz | wc -l

  - Once Marker BLAST Annotation has been run, the BLAST Metrics tab in [Scatter Plot](../#/documentation/VisualizeWorkflowResults--scatter-plot) will include data about each marker. 

### 4. Transpose Data into Marker-Dominant Files
- **[ProjectDir]/transposed**
  - Contains **.mdRAF** files, which are marker dominant files.
  - **.sampRAF** structure:
    - Sample1	Marker1
    - Sample1	Marker2
    - Sample2	Marker1
    - Sample2	Marker2
  - **.mdRAF** structure:
    - Marker1	Sample1
    - Marker1	Sample2
    - Marker2	Sample1
    - Marker2	Sample2
- **transposed/outliers.ser**
- Having data duplicated between sample dominant and marker dominant files allows Genvisis to search files and present data faster depending on whether one sample and all of its markers are being examined (as in [Trailer Plot](../#/documentation/VisualizeWorkflowResults--trailer-plot)) or one marker across all samples is being examined (as in [Scatter Plot](../#/documentation/VisualizeWorkflowResults--scatter-plot)).
