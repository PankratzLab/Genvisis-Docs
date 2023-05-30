Some steps will be flagged as already completed. These are noted below with **Output Already Exists!**

_<span style="text-decoration:underline;">Underlined steps are required for CNV calling.</span>_ Other steps are optional.



1. _<span style="text-decoration:underline;">Transpose Marker Files to Sample Files</span>_
    * Will create **sampRAF** iles in **/samples**
2. Run Marker BLAST Annotation
    * **Output Already Exists!**
3. _<span style="text-decoration:underline;">Compute Sample QC Metrics</span>_
4. _<span style="text-decoration:underline;">Identify Excluded Samples</span>_
5. Generate AB Lookup File
    * **Output Already Exists!**
6. Run Sex Checks
7. Create PLINK Genotype Files
    * **Output Already Exists!**
8. Run GWAS QC
    * **Output Already Exists!**
9. _<span style="text-decoration:underline;">Annotate Sample Data File</span>_
10. Identify Mosaic Chromosomal Arms
11. _<span style="text-decoration:underline;">Compute Population BAF files</span>_
12. _<span style="text-decoration:underline;">Create Sex-Specific Centroids; Filter PFB file</span>_
13. Compute GCMODEL File 
    * **Output Already Exists!**
14. _<span style="text-decoration:underline;">Call CNVs</span>_
    * Change **8. Output filename** to **cnvs/genvisisPC#.cnv**
15. _<span style="text-decoration:underline;">Filter CNVs</span>_
    * Change 1.1 to **cnvs/genvisisPC#.cnv**
    * Change 9 to **cnvs/filteredPC#.cnv**
16. _<span style="text-decoration:underline;">Process CNVs and Create HMM File</span>_
    * Part 2.2 defaults to **cnvs/genvisis.cnv**. Change to **cnvs/filteredPC#.cnv**.
    * Part 6: Output HMM filename change to **hmm/genvisisPC#.hmm**
17. Generate Genotype Mask
18. Run Marker QC Metrics
19. Run Ancestry Checks
20. Run Further Analysis QC
21. Identify Problematic Markers
22. Create Mitochondrial Copy-Number Estimates File
23. Create VCF Files for Imputation
