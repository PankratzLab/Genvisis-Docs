# Create a New Project From .gtc and .idat Files

Follow these instructions if you are starting from scratch with .idat files. 

1. Go to *File > New Project > Genotyping*.
2. A pop-up window will explain which assays are supported. Click **Next**.
3. In **Projects Repository**, choose a folder for the project.
4. Under **Project Name**, select **Create** and name the project.
5. Click **Next**.
6. There will be two options for delineating files with sample intensities:
    * Use sample sheet to load sample intensities
    * Load sample intensities by selecting directories with intensity files
7. In the next window is a text field called SNP Manifest. Point it to a .bpm file on your system that matches the exact version of the array that was used for genotyping. You may already have one in the same directory as the .idat files. If not, you have two options:
    * Download one from Illumina’s website.
    * Search the internet. For example, here is the 1000G project .bpm file.
8. In the Data Repository field, do not select a directory containing the .gtc and .idat files. Select one directory up. You will usually have multiple directories, each representing a sample and each containing numerous .gtc and .idat files. This list of directories will appear in Directories in Repository. Use Add => to move directories that you want to analyze to Selected Directories.
9. Click Next.
10. In the next window, check boxes to Cluster SNPs and Calculate Sample and SNP Statistics
The Gen Call Threshold (used to determine if a genotype is called as missing or not) has a default value of 0.15. This is usually fine. It can be set to 0.25 if you only want to keep higher quality genotypes.
11. The Pre-Calculate option will only be more efficient if you have enough RAM to hold the entire project (i.e., the data for all .idat files) in memory at once. Unfortunately, this can take some trial and error to know for sure. This option will cause the initial project creation to take longer (somewhere on the order of 4x longer), but later calculations in GenomeStudio will be faster (it’s not clear by how much, however). This option only applies to initial project creation and isn’t relevant for an existing project.
12. Click Finish. GenomeStudio will begin loading the samples and building the project. This can take hours or days depending on the size of the project.
