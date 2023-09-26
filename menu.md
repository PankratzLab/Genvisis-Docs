# Menu
* File
    * New Project
    * Import Project
    * Select Project
    * Delete Project
    * Project Properties Editor
    * Open Project Directory
    * Preferences
    * Check for updates
    * Exit
* Data
    * Audit Linker and Pedigree files
    * Audit Samples and Markers (generate paragraph)
    * Map .csv files to IDs
    * Add data to SampleData
    * Genvisis Project Workflow
* Quality
    * Scan for CNPs
    * Filter marker metrics
    * Tally marker annotations
    * Tally without determining dropped markers (much faster)
    * Tally all clustered markers
* Plots
    * Scatter Plot
    * Trailer Plot
    * Comp Plot
    * Mosaic Plot
    * Ancestry Plot
    * Sex Plot
    * 2D Plot
    * QQ Plot
    * Forest Plot
    * Manhattan Plot
* Tools
    * Export to PLINK format
        * Generates PLINK files using the FID/IID IDs in linker.txt
        * Exports only high quality samples and no duplicates
        * In contrast, the Create PLINK Files step generates files using a DNA/DNA scheme that the Run GWAS QC step requires, and includes all samples.
        * Inputs
            * Pedigree File
            * Target Markers FIle
                * A list of markers to base the PLINK files on.
                * One marker per row.
                * Markers in the project, but not in the target file, will be ignored.
                * Leave this option blank to use all markers in PLINK file generation.
            * Cluster Filter File
                * The list of cluster filter files is generated from any file ending with “*clusterFilters.ser” in the project’s data/ directory. The clusters can be manually added from within the ScatterPlot module.
            * AB Lookup File
            * Export Filetype
                * Export files as text or binary
            * PLINK Output Fileroot
                * Files will be generated with this name.
                * Eg. plink will generate plink.bim, plink.bed, plink.fam.
                * Eg. plink/subset/plink will generate a sub directory named subset/ containing plink.bim, plink.bed, plink.fam.
                * There is an Overwrite option that will replace pre-existing files with the same name.
            * GC Cutoff
                * The minimum GC quality score for a sample to be exported.
                * Default is 0.15.
    * Export to VCF format [DEPRECATED]
    * Export for imputation [DEPRECATED]
    * Generate PennCNV files
    * Compute MedianLRR for Regions
    * Parse raw PennCNV results files
    * Parse BPM to CSV file
    * Compute custom centroids file
    * De Novo CNV
    * Export CNVs to Pedfile format
    * Parse workbench files
    * Principal Components
        * Generate Manhattan Plots
        * Generate PC crosstabs
        * Generate data column matrix
    * Generate a demo package
* Help
    * Contents
    * Search
    * About
