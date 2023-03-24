### Affymetrix Data Sets

1. Create Marker Positions
    * Requires an Affymetrix Manifest file
        * **.genvisis/resources/Arrays/AffySnp6/GenomeWideSNP_6.na35.annot.csv** will automatically load from the pre-existing Genvisis resources.
        * This is an hg19 array
        * The array can be lifted over to the human genome version specified at project creation; otherwise, the HG version of a manifest can be found in the header data of the file. To perform the liftover,
            1. Check 2.1 
            2. Select **HG19 **in 2.2 if using **GenomeWideSNP_6.na35.annot.csv**
