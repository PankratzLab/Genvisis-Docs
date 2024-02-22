## PC Corrected Project Workflow

The PC Corrected Project has a slightly different workflow layout than a baseline Genvisis project.

Some steps will be flagged as already completed. These are noted below with **Output Already Exists!** _<span style="text-decoration:underline;">Underlined steps are required for CNV calling.</span>_ All other steps are optional.

1. _<span style="text-decoration:underline;">Transpose Marker Files to Sample Files</span>_
    - Will create **sampRAF** files in **/samples**
2. Run Marker BLAST Annotation
    * **Output Already Exists!**
3. Compute GCMODEL File
    * **Output Already Exists!**
4. _<span style="text-decoration:underline;">Compute Sample QC Metrics</span>_
5. _<span style="text-decoration:underline;">Identify Excluded Samples</span>_
6. _<span style="text-decoration:underline;">Run Sex Checks</span>_
7. Generate AB Lookup File
    * **Output Already Exists!**
8. _<span style="text-decoration:underline;">Create PLINK Genotype Files</span>_
9. _<span style="text-decoration:underline;">Run GWAS QC</span>_
10. Run Ancestry Checks
11. _<span style="text-decoration:underline;">Annotate Sample Data File</span>_
12. _<span style="text-decoration:underline;">Compute Population BAF files</span>_
13. _<span style="text-decoration:underline;">Create Sex-Specific Centroids; Filter PFB file</span>_
14. _<span style="text-decoration:underline;">Call CNVs</span>_
15. _<span style="text-decoration:underline;">Filter CNVs</span>_
16. _<span style="text-decoration:underline;">Process CNVs and Create HMM File</span>_
17. _<span style="text-decoration:underline;">Calls CNVs</span>_
18. _<span style="text-decoration:underline;">Filter CNVs</span>_
19. Generate Genotype Mask
20. Run Marker QC Metrics
21. Run Further Analysis QC
22. Identify Mosaic Chromosomal Arms
23. Identify Problematic Markers
24. Create Mitochondrial Copy-Number Estimates File
25. Create VCF Files for Imputation
