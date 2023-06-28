# PRIMUS 

PRIMUS can help automatically resolve complex pedigree relationships. If you have familial relationships beyond parental and sibling, we recommend using PRIMUS to automatically detect them. PRIMUS will analyze the **plink.genome** file from your Genvisis project and develop a relationship network, identifying parents, children, siblings, cousins, aunts and uncles, grandparents, etc.

1. [Download PRIMUS](https://primus.gs.washington.edu/primusweb/res/form.html).
2. Open the tarball file.
3. Navigate to the file PRIMUS_v1.9.0/bin/run_PRIMUS.pl
4. PRIMUS will take several hours to run. The above file should be run in a high performance computing environment with the command:
./run_PRIMUS.pl -t 0.1 --plink /path/to/plink.genome
    * -t is a parameter to set the minimum level of relatedness for two people to be considered related (default=0.1).
    * The results directory will be located in the same place as your plink.genome file, named plink.genome_PRIMUS.
