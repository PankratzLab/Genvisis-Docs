# QQ Plot

QQPlot implements a standard way of visualizing a distribution of p-values. Ideally a p-value distribution for all the genetic variants (black dots) will form a tight line with the expected distribution of random chance (gray line) until the very end where it will deviate if the study has any significant findings.

QQ plot compares observed p-values from a GWAS to hypothesized p-values. A straight line distribution indicates a close 1:1 correlation. The more observed values deviate from hypothesized values, the more they will curve away from the hypothesized line. 

The lambda from the data is calculated and printed onto the QQ plot. Ideally, lambda should be ~1.0. Deviations, usually at the lower end of p-values, can indicate significant hits. Filtering for rare variants at MAF <5% is best practice.

Takes as input a file with a header and at least two columns - SNP and p-value:

    SNP    P-value
    rs6012681    0.4427
    rs6012683    0.4384
    rs6012686    0.4229

The SNP column doesn't need to contain any specific information, such as chromosome or position.

Alternatively, QQ Plot can take a file with a header and at least three columns - chromosome, position, and p-value:

    Chr  	Pos  	P-value
    1   	12541586 0.4427
    1   	13576290 0.4384
    2   	11273187 0.4229

The chromosome column must contain integers (eg. "chr1" will cause an error).  This three column file can also be used in [Manhattan Plot](../#/documentation/VisualizeWorkflowResults--manhattan-plot).

The column order in the input files doesn’t matter and there can be additional columns; Genvisis will detect the p-value column.

A QQ Plot of frequency instead of p-values can be made by not including a p-value column:

    SNP    Freq
    rs6012681    0.6873
    rs6012683    0.0011
    rs6012686    0.9955

A QQ Plot can also be generated from the command line with:
java -jar genvisis.jar org.genvisis.cnv.plots.PlotUtilities results=[input file to parse] qq=TRUE qqMinMAF=0.05

The input file at the command line requires 3 columns - marker name/snp, p-values, and frequency:

    MarkerName    P-value    Freq
    chr11:12541586:A:G    0.4427    0.6873
    chr8:102803998:G:A    0.8713    0.0011
    chr13:55101557:T:C    0.9473    0.9955

The marker name/snp column either must contain chromosome and position information, or a map file has to be included separately (eg. map=plink.bim). Frequency can also be included in a separate file (eg. freq=plink.frq). The column order in the input files doesn’t matter and there can be additional columns.  The results files from SNPTest (combined.results) or METAL (*\_InvVar1.out) can be used as input with no changes necessary.  The output is **[input\_file]\_topmed\_rebuild\_QQ\_data\_qqPlot\_MAF\_Filtered.png**.
