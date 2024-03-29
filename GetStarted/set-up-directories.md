# Set Up Directories
Create a directory in which your project will be stored (this main diretory will be referred to as **[ProjectDir]** for the rest of the documentation). Inside, create two sub-directories named **00src** and **data**.

### **00src/**
This sub-directory stores your raw/source data files (GenomeStudio Final Report files for Illumina data [either **.csv** or **.csv.gz** format] or **.CEL** files for Affymetrix data) and can be named whatever you wish. We will use **00src/** throughout this documentation. No other files should be included in this directory.

### **data/**
This sub-directory stores several required and optional files. It must be named **data/** for Genvisis to work properly.

Save your **[pedigree.txt](../#/documentation/GetStarted--set-up-pedigree-and-linker)** and **[linker.txt ](../#/documentation/GetStarted--set-up-pedigree-and-linker)** files in this sub-directory.

Save your batch file (optional) in this sub-directory. If your samples were genotyped in batches, a batch file allows you to specify the groups in which they were genotyped. Genvisis can then detect whether a batch has such significant batch effects that it should be reclustered by itself. The batch file is a **.txt** file that should list the sample ID (the same ID used in the **DNA** column of **linker.txt**) in the first column and an ID for its batch in the second column. There is no header. For example:
   ```
                ID001 Batch1
                ID002 Batch1
                ID003 Batch2
                ID004 Batch2
                ID005 Batch3
                ID006 Batch3
   ```

Save your marker subset file (optional) in this sub-directory. If your source data files do not contain every marker present in the manifest, or if they contain markers that are not in the manifest, this file can be used to specify the markers that are shared between the manifest and source files (i.e., the markers that Genvisis should use). The marker subset file is a **.txt** file that lists the marker names in a single column with one marker for line. There is no header.

### **Manifest** (Illumina data only)
For Illumina data, store the manifest file (the **.csv** version with probe sequences) in your **[ProjectDir]**. The manifest file unlocks many important features; if a manifest is not available or does not contain probe sequences, a GenomeStudio **SNP_Map.csv** file (which is created alongside the final reports) can be used instead.
