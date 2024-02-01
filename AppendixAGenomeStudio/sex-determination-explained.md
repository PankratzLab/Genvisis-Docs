# Explanation of Sex Determination

## GenomeStudio 2.0.2 and previous versions
For Infinium products, GenomeStudio performs the sex estimate by collect all SNPs on the X locus and then counting the AB genotypes for this subset. If there are fewer than 20 total SNPs on the X chromosome, the sex call is unknown. If there are at least 20 SNPs on X and if the percent of AB is 10% or greater, the sex call is female. If there are at least 20 SNPs on X and if the percent of AB is less than 10%, the sex call is male. The accuracy of the sex estimation may vary depending on the coverage (i.e., the number of SNPs on the X chromosome).
  
## GenomeStudio 2.0.3+
Genome Studio counts all autosomal loci and Y loci; if there are fewer than 100 autosomal loci or fewer than 20 Y loci, Genome Studio defaults to older Gender Est algorithm. Otherwise, if the call rate of the autosomal loci is less than 0.97, the sex call is unknown. If the median Y intensity is greater than 0.3, the sex call is male; otherwise, Genome Studio goes to the next step. If the median X intensity is less than 0.9, the sex call is unknown; otherwise, the sex call is female.

Genvisis will more accurately estimate sex, including delineating which samples have aneuploidies (Klinefelter syndrome (47,XXY), Triple X syndrome (47,XXX), and Turner syndrome (45,X), including mosaic versions thereof). Thus it is not critical that the GenomeStudio determination be completely accurate.
