# ManhattanPlot

A Manhattan plot is a standard way of visualizing a genome-wide association study (GWAS) that makes it easy to see the strongest genetic signals and the support they have from variants in linkage disequilibrium with them. Specifically, a Manhattan plot shows the p-values for variants included in a GWAS. It is a helpful check to see any hits and any significant regions, as well as to see the general distribution of p-values for your data. The plot displays a threshold of 10<sup>-5</sup> and a significant threshold of 10<sup>-8</sup>.  

In Genvisis, ManhattanPlot takes as input a file with a header and at least three columns: chromosome, position, and p-value. For example,

    Chr      Pos          P-value
    1        12541586     0.4427
    1        13576290     0.4384
    2        11273187     0.4229

The chromosome column must contain only integers (e.g., "chr1" will cause an error). Additional columns in the file will be listed in the **Load File** pop-up window; use the accompanying checkboxes to turn on each column if desired. ManhattanPlot also has a **P-Value Filter** (default <span>&#8804;</span> 0.05) and a **Select Chrs**: column (the default is to load all chromosomes except for chr0 and unknown chromosomes).

This three-column input file can be used in [QQPlot](../#/documentation/VisualizeWorkflowResults--qq-plot) as well.

From the command line, you can direct Genvisis to generate a Manhattan Plot via the following command:

    java -jar genvisis.jar org.genvisis.cnv.plots.PlotUtilities results=[input file to parse] manhattan=true hitwindows=true

For the command line version of ManhattanPlot, the input file requires three columns: marker name/SNP, p-value, and frequency. For example,

    MarkerName            P-value   Freq
    chr11:12541586:A:G    0.4427    0.6873
    chr8:102803998:G:A    0.8713    0.0011
    chr13:55101557:T:C    0.9473    0.9955

The marker name/SNP column must contain chromosome/position information or a map file must be included separately (e.g., **map=plink.bim**). Frequency can also be included in a separate file (e.g., **freq=plink.frq**). The column order in the input files does not matter, and there can be additional columns. The results files from SNPTest (**combined.results**) or METAL (***\_InvVar1.out**) can be used as input with no changes necessary. The output file is named **[input\_file]\_topmed\_rebuild\_Manhattan\_data\_manPlot.png**.
