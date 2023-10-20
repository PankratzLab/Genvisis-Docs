## Call CNVs Using Optimized HMM File

#### 1. Process CNVs and Create HMM File step [process-cnvs-hmm] must have been run already or must be selected

#### 2.1 Compute Population BAF Files step [compute-pfb] must have been run already or must be selected

#### 2.2 PFB File Must Exist

#### 3.1 Compute GCMODEL File step [gcmodel] must have been run already or must be selected

#### 3.2 GCMODEL File Must Exist

#### 4 CNV Calling Scope
* AUTOSOMAL: Chromosomes 1 to 22
* SEX CHROMOSOMES: Chromosomes 23 (X) and 24 (Y)
* BOTH (default): Calls AUTOSOMAL and SEX CHROMOSOMES

#### 5 (optional) If calling chromosomal CNVs, use sex-specific centroids to recalculate LRR/BAF values?

#### 6.1 (optional) Use Genvisis-generated list of markers to ignore (if it exists)

#### 6.2 (optional) File of problematic or dropped markers to ignore in CNV calling

#### 7 Number of threads

#### 8 Output filename (must not already exist)