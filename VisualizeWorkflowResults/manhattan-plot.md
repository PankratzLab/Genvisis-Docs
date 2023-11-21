# ManhattanPlot

ManhattanPlot implements a standard way of visualizing a genome-wide association study (GWAS) and makes it easy to see the strongest genetic signals and the support they have from other variants that are in linkage disequilibrium with them.

ManhattanPlot shows the p-values for variants included in a GWAS. It is a helpful visual check to see any hits and any significant regions, as well as to see the general distribution of p-values for the data. The plot displays a threshold of 10<sup>-5</sup> and a significant threshold of 10<sup>-8</sup>.  

ManhattanPlot takes as input a file with a header and at least three columns; chromosome, position, and p-value. For example,

    Chr  	Pos  	P-value
    1   	12541586 0.4427
    1   	13576290 0.4384
    2   	11273187 0.4229

The chromosome column must contain only integers (e.g., "chr1" will cause an error). Additional columns in the file will be listed in the **Load File** pop-up window; use the accompanying checkboxes to turn on each column if desired. ManhattanPlot also has a **P-Value Filter** (default <= 0.05) and a **Select Chrs**: column (the default is to load all chromosomes except for chr0 and unknown chromosomes).

This three column input file can be used in [QQ Plot](../#/documentation/VisualizeWorkflowResults--qq-plot) as well.

A Manhattan Plot can also be generated from the command line with:

    java -jar genvisis.jar org.genvisis.cnv.plots.PlotUtilities results=[input file to parse] manhattan=true hitwindows=true

The input file at the command line requires 3 columns - marker name/snp, p-values, and frequency:

    MarkerName    P-value    Freq
    chr11:12541586:A:G    0.4427    0.6873
    chr8:102803998:G:A    0.8713    0.0011
    chr13:55101557:T:C    0.9473    0.9955

The marker name/snp column either must contain chromosome and position information, or a map file has to be included separately (eg. map=plink.bim). Frequency can also be included in a separate file (eg. freq=plink.frq). The column order in the input files doesn’t matter and there can be additional columns. The results files from SNPTest (combined.results) or METAL (*\_InvVar1.out) can be used as input with no changes necessary. The output is  **[input\_file]\_topmed\_rebuild\_Manhattan\_data\_manPlot.png**.
