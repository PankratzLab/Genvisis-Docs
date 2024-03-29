## Run Sex Checks

We want to avoid regions on chrX that have homologies on chrY (beyond the pseudoautosomal regions that are already known to be homologous).

To do so,
1. provide a file listing one hit wonders (markers that map to one location on a genome and nowhere else)
2. take information from the BLAST annotation in Step 3
3. check the box to “Use only X and Y chromosome R values to identify sex discriminating markers”

If you do not have either a manifest file that contains probe sequences (for Illumina) or a *.probe_tab file (for Affymetrix), then select the checkbox for requirement 3.3 to use R values to identify sex-discriminating markers.

