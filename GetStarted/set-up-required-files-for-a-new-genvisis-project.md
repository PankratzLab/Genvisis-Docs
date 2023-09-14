# Set Up Directories

Create a directory/folder in which your project will be stored. Inside, create two sub-directories named **00src** and **data**.
Place your project files in these locations:

* **00src/** 
    * This is the directory for your raw/source data files.
    * These will either be GenomeStudio Final Report files for Illumina data or .CEL files for Affymetrix data.
    * No other files should be included in this directory.
* **data/**
    * **[pedigree.txt](../#/documentation/GetStarted--set-up-pedigree-and-linker)**
    * **[linker.txt ](../#/documentation/GetStarted--set-up-pedigree-and-linker)**
    * **Batch file** (optional)
        * .txt file
        * If samples were genotyped in batches, this file allows you to specify the groups.
        * With no header, list sample ID (the same ID used in the **DNA** column of linker.txt) in the first column and an ID for its batch in the second.
          * Example
    
              ID001 Batch1
              ID002 Batch1
              ID003 Batch2
              ID004 Batch2
              ID005 Batch3
              ID006 Batch3

       * This allows Genvisis to detect whether a batch has such significant batch effects that it should be reclustered by itself.
  * **Marker subset file** (optional)
     * .txt file
     * If your source data files do not contain every marker present in the manifest, or contain markers that are not in
    the manifest, this file can be used to specify the shared subset of markers between the manifest and source files that Genvisis should use.
     * With no header, list marker names in a single column, one marker per line.
* **Manifest** (Illumina data only)
    * .csv version with probe sequences.
    * Stored in the main project directory.
    * This file unlocks many important features, but a GenomeStudio **SNP_Map.csv** file can be used instead if a manifest is not available.
