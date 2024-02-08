# Resources Directory
When you first create a Genvisis project, Genvisis will create a resources directory, **.genvisis/**, in your home directory. This directory contains files that are used across Genvisis projects.
    * Linux/Mac: $HOME/.genvisis/
    * Windows: C:\Users\[username]\.genvisis\

The **.genvisis/** directory contains the following sub-directories and files.
    * example/
    * projects/ (contains **.properties** files for each project created)
    * resources/
        * Arrays/
            * AffySnp6/ (contains Affymetrix arrays and support files)
        * CNV/ (contains Hidden Markov Model [**.hmm**] files used in CNV calling)
        * Genome/ (contains resource files for human genome builds hg18, hg19, and hg38)
        * HapMap/ (contains resource files for HapMap samples)
    * custom_path (the full path of **.genvisis/**)
    * Launch.bat (running this file will launch Genvisis on a Windows machine)
    * Launch.command (running this file will launch Genvisis on a Linux/Mac machine)
    * launch.properties (contains properties used by all Genvisis projects; for example, the path to PLINK, the location of resources/, the location of projects/, record of the last project opened, etc.
    * Launch.sh
Running this file will launch Genvisis on a Unix/Linux/Mac machine