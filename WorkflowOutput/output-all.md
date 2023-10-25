# Workflow Output for All Array Types

### 5. Compute GCMODEL File
- **[ProjectDir]/data/SampleData.txt**
- **[ProjectDir]/data/custom.gcmodel**
  - Lists the average GC content for every probe.

### 6. Compute Sample QC Metrics
- **lrr\_sd.xln**
- Each row in the file is a sample. Each column is a QC metric.
  - LRR\_AVG - Average log R ratio or average intensity
    - Tells us about the relative amount of DNA compared to other samples
    - Log R ratio is population normalized
  - LRR\_SD
    - Standard deviation of the LRR average
    - If standard deviation is high, this is an indication that it’s a low quality sample
    - Start worrying when LRR\_SD is above 0.32. Beyond 0.5 is a sample failure.
  - LRR\_SD\_-2.0\_2.0
    - LRR\_SD calculated only from markers within the range of -2.0 to 2.0
  - Genotype\_heterozygosity 
    - Also known as genotype call rate
    - Sample is low quality if this drops below 0.95 (or below 0.98 in an Illumina dataset because Illumina uses longer probe sequences of 50bp, as opposed to 25bp in Affymetrix, which leads to higher quality intensity and less noise)
  - LRRMedians per chromosome
    - Adds chromosome median\_chr# columns for chr0 to chr24
- **audit/ExcludesUsing25lrrsd98callrate3bafsd.xln**
- Additional ExcludesUsing… files
  - An ExcludesUsing… file can be imported into GenomeStudio to exclude samples for Phase 3 clustering and CNV calling.
- **audit/ExploreThresholds.out**
  - Describes how many samples were excluded under different thresholds and rates the quality of the data set based on this (high quality, low quality, or very low quality).
- **results/Mosaicism.naive.xln**
- **results/Mosaicism.naive.agnostic.xln** 
- **results/Mosaicism.naive.agnostic.xln.filtered**
- **results/Mosaicism.naive.forceCall.xln**
- **results/Mosaicism.naive.genomeSummary.xln**

### 7. Identify Excluded Samples
- Adds two columns to the file [ProjectDir]/data/SampleData.txt
  - CLASS=EXCLUDE (0 or 1)
  - ExcludeNote (a description of why the sample was excluded)
- **[ProjectDir]/audit/ExcludedSamples.xln**
  - Contains columns Sample ID, Exclude, ExcludeNote, LRR\_SD, Genotype\_callrate, and BAF1585\_SD.

### 8. Run Sex Checks
- [ProjectDir]/data/SampleData.txt
- [ProjectDir]/results/sexCheck.xln
- [ProjectDir]/results/sexCheck\_regions.txt
- Adds the following columns to SampleData.txt
  - CLASS=Sex
  - CLASS=Estimated Sex

### 9. Generate AB Lookup File
- **[ProjectDir]/AB\_lookup\_parsed.dat**

### 10. Create PLINK Genotype Files
- [ProjectDir]/plink
  - plink.fam
    - FID (Family ID)
    - Within Family ID (IID)
    - Within Family ID of father (0 if father not in dataset)
    - Within Family ID of mother (0 if mother not in dataset)
    - Sex Code
      - 1 = male
      - 2 = female
      - 0 = unknown
    - Phenotype Value
      - 1 = control
      - 2 = case
      - -9/0/non-numeric = missing data if case/control
  - plink.bed
    - Primary representation of genotype calls at biallelic variants
  - plink.bim
    - All of the markers in the data set
- Note: The FID and IID columns in the plink files use the id in the DNA column of linker.txt and not FID/IID. This is counterintuitive, but is done because Run GWAS QC requires the DNA id to work. The Export to PLINK format command under Tools will generate files with the expected FID/IID ids.
- The files made in this step contain all samples and all markers. No filtering is performed.

### 11. Run GWAS QC
- [ProjectDir]/plink/quality\_control/
  - [ProjectDir]/plink/quality\_control/marker\_qc/
    - Data generated in this directory include files where individuals with more than 20% of the genome not having a valid call are removed, markers with similarly bad problems are removed, allele frequency check, check by missingness (missingness.imiss is based on the individual, missingness.lmiss is based on the locus or marker), and Hardy-Weinberg equilibrium is computed (hardy.hwe) under the assumption that all individuals are being used. This step determines the minimal set of useful markers and then LD prunes those for relationship and ancestry checks.
    - marker\_qc/miss\_drops.dat
      - A list of markers to drop
    - marker\_qc/miss.out
      - A summary of why they were flagged to be dropped
  - [ProjectDir]/plink/quality\_control/sample\_qc/
  - [ProjectDir]/plink/quality\_control/genome/
    - plink.genome
      - [File description](https://www.cog-genomics.org/plink2/formats#genome)
      - A pairwise comparison of all individuals
      - If two individuals are not related, Z0 column should be close to 1.0 (percentage of markers not in the same ancestor)
      - If a parent-offspring pair, Z1 expected to be close to 1.0 (meaning one of the two alleles is consistently shared between the individuals)
      - For sibling relationship, Z0 = 0.25, Z1 = 0.5, Z2 = 0.25
      - Identical twins or a blind duplicate will have Z2 = 1.0 and PI\_HAT = 1.0 (the total percentage of the genome that is identical)
    - plink.genome\_relateds.xln
      - A filtered version of plink.genome
      - The column Type lists relationships, such as duplicate, parent-offspring, or avuncular,grandparent,halfsibs
      - Samples that were redone by the original lab usually have \_001 and \_002 in their IDs, or \_redo or \_duplicate. Check for this when seeing duplicates.
      - The CALLRATE columns are used to determine which of the duplicates are used in the analysis. The smaller the CALLRATE value, the lower the missingness rate. Genvisis chooses the duplicate with the smaller CALLRATE value. The columns FID\_KEEP, IID\_KEEP, FID\_DROP, and IID\_DROP identify which samples were kept and which were dropped, respectively.
  - [ProjectDir]/plink/quality\_control/ld\_pruning/
  - [ProjectDir]/plink/quality\_control/ancestry/
    - Contains the standard PLINK trio of .bed, .bim, and .fam
    - These contain a smaller set of markers that have been ld pruned.
    - We want markers that are independent, otherwise ld patterns can manifest themselves and principal components will pick up on that.
    - unrelateds.txt 
      - A list of unrelated samples. 

### 12. Run Ancestry Checks
- [ProjectDir]/plink/quality\_control/ancestry/plink.bim\_unambiguous.txt
  - A list of unambiguous SNPs (throws out A-T and G-C matches). These are compared to the SNPs in ancestry/unambiguousHapMap.bim.
- ancestry/combo1.missnp
  - Any SNPs that are missed in the merging of unambiguous SNPs and HapMaps. These are SNPs that are A-C in one and T-G in another. SNPs are automatically flipped in one of the data sets so that they match up.
- ancestry/combo2.misssnp
  - Merging is repeated and any SNPs that are still missed go here. SNPs that are still missing at this point are probably a tri-allelic marker (eg. G>A,T or G to A in one dataset and G to T in another). The rsID can be searched on [dbSNP](https://ncbi.nlm.nih.gov/snp/) to verify this.

### 13. Annotate Sample Data File
- Adds additional columns to data/SampleData.txt
  - DuplicateId
  - Use
  - UseNote
  - Use\_cnv
  - Use\_cnvNote
  - mzTwinID
- Also runs relationship checks and produces:
  - [ProjectDir]/relationshipChecks.xln
  - discrepantRelationships.xln
  - trios.xln

### 14. Compute Population BAF files
- data/custom.pfb

### 15. Create Sex-Specific Centroids; Filter PFB file
- data/sexSpecific\_Male.cent
- data/sexSpecific\_Male.cent.txt
- data/sexSpecific\_Female.cent
- data/sexSpecific\_Female.cent.txt

### 16. Call CNVs
- AUTOSOMAL Calling Scope:
  - [ProjectDir]/cnvs/genvisis.cnv
- SEX CHROMOSOMES Calling Scope:
  - cnvs/genvisis\_23F.cnv
    - Chromosome X female
  - cnvs/genvisis\_23M.cnv
    - Chromosome X male
  - cnvs/genvisis\_24M.cnv
    - Chromosome Y
- BOTH calling Scope
  - genvisis\_all.cnv

### 17. Filter CNVs
- [ProjectDir]/cnvs/filtered.cnv
- filtered.cnv.ind.ser.gz
  - An index used in [Trailer Plot](../#/documentation/VisualizeWorkflowResults--trailer-plot).
- cnvs/cnvsByLrrSd/
  - genvisisCnvsByLrrSd.xln
  - genvisisCnvsByLrrSd.png
  - filteredCnvsByLrrdSd.xln
  - filteredCnvsByLrrdSd.png
    - These files list the LRR\_SD, LRR\_SD\_-2.0\_2.0, and CNV count for each sample. The .xln files can be loaded into [Custom Plot](../#/documentation/VisualizeWorkflowResults--custom-plot) to visualize the relationship between LRR\_SD and number of CNVs called per sample.
    - The .png files are 2D Plots of the CNV counts by LRR\_SD for quick reference. Use 2D Plot for higher resolution.
    - As the number of CNV calls increases, more are being identified, but there is a tipping point where too many CNV calls are most likely false positives (a rule of thumb is to treat CNV counts < 100 as real).
    - The filtered CNV counts can be used to refine the LRR\_SD threshold in Step 8: Identify Excluded samples, to further improve CNV calling.

### 18. Process CNVs and Create HMM File
- [ProjectDir]\hmm\genvisis.hmm 
  - Contains average values for all markers with a copy number of 1, 2, etc., giving parameters customized to the data
- cnvs\genvisisHMM.cnv and cnvs\filteredHMM.cnv
  - If 7: (optional) Call CNVs with new HMM file was checked

### 19. Call CNVs Using Optimized HMM File
- AUTOSOMAL Calling Scope:
  - [ProjectDir]/cnvs/genvisisHMM.cnv
- SEX CHROMOSOMES Calling Scope:
  - cnvs/genvisisHMM\_23F.cnv
    - Chromosome X female
  - cnvs/genvisisHMM\_23M.cnv
    - Chromosome X male
  - cnvs/genvisisHMM\_24M.cnv
    - Chromosome Y
- BOTH calling Scope
  - genvisisHMM\_all.cnv

### 20. Filter Optimized CNVs
  - [ProjectDir]/cnvs/filteredHMM.cnv
  - cnvs/cnvsByLrrSd/
    - genvisisHMM\_allCnvsByLrrSd.xln
    - genvisisHMM\_allCnvsByLrrSd.png
    - filteredHMMCnvsByLrrSd.xln
    - filteredHMMCnvsByLrrSd.png

### 21. Identify Samples To Use In CNV Analysis
- [ProjectDir]/output/cnv\_analysis.fam 

### 22. Run CNV Analysis Pipeline
- [ProjectDir]/cnv\_analysis
  - [Model Label].cnv
  - results/
    - *.confPosition.out
    - *.confWindow.out
  - [FAM File Label]/
    - [Model Label]/
      - conf.cnv
      - conf.cnv.grp.summary
      - conf.cnv.indiv
      - conf.cnv.map
      - conf.cnv.summary
      - conf.cnv.summary.mperm
      - conf.fam
      - conf.log
      - confPosition
      - confPosition.cnv.indiv
      - confPosition.cnv.summary
      - confPosition.cnv.summary.mperm
      - confPosition.hits
      - confPosition.hits.regions.txt
      - confPosition.log
      - confPosition\_manPlot.png
      - confPosition.out
      - confPosition.out.map
      - confWindow
      - confWindow.cnv.indiv
      - confWindow.cnv.summary
      - confWindow.cnv.summary.mperm
      - confWindow.hits
      - confWindow.hits.regions.txt
      - confWindow.log
      - confWindow\_manPlot.png
      - confWindow.out
      - confWindow.out.map

### 23. Generate Genotype Mask
- [ProjectDir]/MendelZeroer/
  - cnv.clst
  - cnv.zero
  - mosaic.clst
  - mosaic.zero
  - zeroMap.txt

### 24. Run Marker QC Metrics
- Produces output in [ProjectDir]/results
  - results/markerQualityChecks.xln contains the quality metrics that were generated and can be used to filter markers as high quality or low quality
    - These metrics are based on intensity data. In contrast, PLINK uses Hardy-Weinberg equilibrium.
    - This file is useful to check for markers having batch effects
      - The column BatchEffect\_BATCH\_n=# contains p-values from a test of batch effects for each sample
        - Eg. If batches are found to have fundamentally different intensities, they can then be reclustered separately
      - The column DuplicateErrors will be populated if you previously flagged duplicates, and can be used to see how many times a duplicate creates an error and inconsistency between duplicates.
      - The column MendelianErrors is used if you have families flagged in the data set.
  - results/markerQualityChecks\_BATCH\_ALLELIC\_batchEffects.out 
    - Only present if a batch file was used.
    - Tests allelic batch effects.
    - Tests whether frequency is different from one group to another. This performs logistic regression by batch/source (e.g. CBP=1 if not =0). 
    - Column reports p-value for marker which indicates difference between the batch/source.
    - If you find significant p-values, you can view the markers in Scatter Plot.
      - File > New Marker List > … next to the field for File Name
      - Chose a location and name for the marker list and hit Save
      - Copy and paste marker names with significant p-values into the Marker names text box.
      - The levels set in the Class=Batch/Source column will be present in the Color code by: toggles below the scatter plot. Samples can be excluded by clicking source name.
    - When mixed colors in the middle X-Y plot > seeing a shift (not causing a problem).
  - results/markerQualityChecks\_BATCH\_MISSINGNESS\_batchEffects.out
    - Only present if a batch file was used.
    - Tests allelic batch effects.
    - Tests if call rate is different by batch/source.
  - markerQualityChecks.mendel
  - combined.criteria
  - exclusion.criteria
  - review.criteria 
  - markersToReview.out
  - markersToExclude.out
  - markersToReviewCombined.out

### 25. Run Further Analysis QC
- [ProjectDir]/plink/quality\_control/further\_analysis\_QC/

### 26. Identify Mosaic Chromosomal Arms
- [ProjectDir]/results/Mosaicism.xln
  - Contains two rows per chromosome per sample, one for each arm (eg. chr6p, chr6q)
  - If there are no markers on the arm, such as the acrocentric chromosomes (chr13, 14, 15, 21, and 22 p-arms), it won’t produce a row for that arm.
  - LRR N - number of markers with a valid LRR value
  - mean LRR
  - BAF N - number of markers with a valid BAF value
  - SD of BAF - 
  - IQR of BAF - Interquartile range; difference between 25th and 75th percentiles
Both BAF columns are measures of dispersion/variance
  - %Homo - percentage of homozygosity. Usually high (above 60%), but very high can indicate uniparental disomy or inbreeding leading to runs of homozygosity
  - ForcedCallArmPercentMosaicism - the result of assuming an entire arm is mosaic and then calculating what percentage of cells have the mosaic event
-1 value if not enough data to make a determination
  - NumberRegionsDetected - Number of mosaic events identified
  - ProportionArmCalledMosaic - mosaicism calls are made using the BAF and the detailed results are in results/Mosaicism.agnostic.xln 
    - BpCalledMosaic and BpInArm are the numerator and denominator for ProportionArmCalledMosaic
- results/Mosaicism.agnostic.xln 
  - Contains results from calling mosaicism on chromosomes based on the B allele frequency
- results/Mosaicism.agnostic.xln.filtered
  - The mosaic calls from Mosaicism.agnostic.xln filtered with a minimum size of 1,000,000, a minimum score of 0.5, and a maximum score of 0.8.
- results/Mosaicism.forceCall.xlnc
- results/Mosaicism.genomeSummary.xln
- results/aneuploidyEvaluation.xln
- This data is visualized with [Mosaic Plot](../#/documentation/VisualizeWorkflowResults--mosaic-plot).

### 27. Identify Problematic Markers
- [ProjectDir]/data/drops.dat

### 28. Generate Principal Components
- [ProjectDir]/PCA/PCA\_GENVISIS

### 29. Create PC-Corrected Project
- [ProjectDir]/pcCorrected\_#PCs\_[correction type]\_[sex chr strategy]
  - Eg. pcCorrected\_20PCs\_XY\_BIOLOGICAL
- This subdirectory contains a new Genvisis project with a /transposed dir containing the PC corrected samples.
  - X and Y are transformed based on the nearest genotype cluster using the number of principal components specified by the user. LRR and BAF are recomputed based on the new X and Y values.
- This new project will appear in the upper right corner of the Genvisis GUI.
  - [You can now run this new project up to cnv calling and optimization a second time](../#/documentation/RunAPCCorrectedProject--overview).

### 30. Create Mitochondrial Copy-Number Estimates File
- [ProjectDir]/
  - PCA\_MITO\_wGC.MitoMarkers.RawValues.txt
  - PCA\_MITO\_wGC.MitoMarkers.MarkersUsed.txt
  - AllMitoMarkers.txt
- [ProjectDir]/PCA/PCA\_MITO\_wGC/
  - PCA\_MITO\_wGC.PCs.extrapolated.txt
  - PCA\_MITO\_wGC.PCs.SingularValues.png
  - PCA\_MITO\_wGC.PCs.SingularValues.txt
  - PCA\_MITO\_wGC.PCs.MarkerLoadings.txt
  - PCA\_MITO\_wGC.PCs.txt
  - PCA\_MITO\_wGC.PCs.MarkerReport.txt
  - PCA\_MITO\_wGC.samples.USED\_PC.txt
  - PCA\_MITO\_wGC.samples.QC\_Summary.txt
  - PCA\_MITO\_wGC\_lrr\_sd.txt
  - PCA\_MITO\_wGC\_markers\_ABCallRate.txt
  - PCA\_MITO\_wGC\_markerQC\_BATCH\_MISSINGNESS\_batchEffects.out
  - PCA\_MITO\_wGC\_markerQC\_BATCH\_ALLELIC\_batchEffects.out
  - PCA\_MITO\_wGC\_markerQC.txt
  - PCA\_MITO\_wGC\_markerQCtmp#.bonferroni.txt
  - PCA\_MITO\_wGC\_markers\_to\_QC.txt
  - PCA\_MITO\_wGC\_baselineMarkers.txt
- [ProjectDir]/PCA/PCA\_MITO\_wGC/PCA\_MITO\_wGC\_GC\_ADJUSTMENT
  - default\_gc\_parameters.GENVISIS\_GC.gc\_Centroids.ser
  - default\_gc\_parameters.GENVISIS\_GC.gc\_Centroids\_TMP\_BAK.ser
  - default\_gc\_parameters.GENVISIS\_GC.ser
  - gc\_Centroids.ser
  - custom.gcmodel.ser

### 31. Create VCF Files for Imputation
- [ProjectDir]/export/genvisis/
  - .vcf.gz and .vcf.gz.tbi files for each chromosome selected.
  - Files that can be analyzed on the [TOPMed Imputation Server](https://genvisis.org/#/documentation/AppendixCTOPMedImputation--topmed-imputation-server).


