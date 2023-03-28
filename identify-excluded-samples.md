### Identify Excluded Samples

This option loads **lrr_sd.xln** and filters out low quality samples.

The user sets thresholds for filtering. Default values are 0.32 for **LRR SD**, 0.95 for **Callrate**, and 3 for **BAF SD**.
- **LRR SD**
  - Phase 2: Set **LRR SD** to 0.5 for SNP analysis.
  - Phase 3: Keep **LRR SD** at the default of 0.32 for CNV analysis.
- **Callrate**
  - 0.98 is the standard **Callrate** for Illumina data.
  - 0.95 is the standard **Callrate** for Affymetrix data.
- **BAF SD** 
  - Can remain at the default of 3 for most projects.
