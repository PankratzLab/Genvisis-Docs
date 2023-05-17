# Set Up Required Files for a New Genvisis Project 

* **00src/** 
    * Directory containing GenomeStudio Final Report files for Illumina data or CEL files for Affymetrix data
* **data/[pedigree.txt](#bookmark=id.3wqz7fyhw1k7)** 
    * Identical to a plink.fam file
    * For some projects everyone will be listed as unrelated
* **data/[linker.txt ](#bookmark=id.3wqz7fyhw1k7)**
    * Text file that maps the Sample ID in Illumina’s GenomeStudio or Affymetrix Power Tools to a family ID (FID) and individual ID (IID)
    * Also delineates who is a duplicate
* **data/batch.txt** 
    * Optional
    * If samples were genotyped in batches, this file allows you to delineate the groups
    * This allows Genvisis to detect whether a batch has such significant batch effects that it should be reclustered by itself
* **Manifest (Illumina data)**
    * .csv version with probe sequences
    * Unlocks many important features, but a GenomeStudio **SNP_Map.csv** file can be used instead
