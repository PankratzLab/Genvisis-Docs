# Explanation of Sex Determination

## GenomeStudio 2.0.2 and previous versions
For Infinium products, GenomeStudio performs the gender estimate in the following manner:
* Collect all SNPs on the X locus.
* Count all the "AB" genotypes for this subset.
* If there are less than 20 total SNPs on the X chromosome, the gender call is Unknown.
* For greater than 20 SNPs on X, if the percent of "AB" is 10% or greater, the gender call is Female.
* For greater than 20 SNPs on X, if the percent of "AB" is less than 10%, the gender call is Male.
* Depending on the coverage (i.e., number of SNPs on the X chromosome), the gender estimation accuracy can vary.

## GenomeStudio 2.0.3+
* Count all autosomal loci and Y loci: if autosomal loci are below 100 or Y loci are below 20, defaults to older Gender Est algorithm
* If Call Rate of autosomal loci is below 0.97, gender call is Unknown.
* If median Y intensity is greater than 0.3, gender call is Male, otherwise, go to next step
* If median X intensity is less than 0.9, gender call is Unknown, otherwise, gender call is Female.

Note that Genvisis will do a better job estimating sex, including delineating which samples have aneuploidies (Klinefelter syndrome (47,XXY), Triple X syndrome (47,XXX), and Turner syndrome (45,X), including mosaic versions thereof). It is therefore not critical that the GenomeStudio determination is completely accurate.
