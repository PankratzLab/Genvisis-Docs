# Resources Directory
* The first time you create a Genvisis project, .genvisis/ will be created in your home directory.
    * Linux/Mac: $HOME/.genvisis/
    * Windows: C:\Users\[username]\.genvisis\
* This directory contains files that are used across Genvisis projects.
* .genvisis/
    * example/
    * projects/
        * .properties files for each project created
    * resources/
        * Arrays/
            * AffySnp6/
Affymetrix arrays and support files
        * CNV/
            * Hidden Markov Model files (.hmm) used in CNV calling.
        * Genome/
            * Resource files for Human Genome builds hg18, hg19, and hg38
        * HapMap/
            * Resource files for HapMap samples
    * custom_path
        * The full path of .genvisis/
    * Launch.bat
        * Running this file will launch Genvisis on a Windows machine
    * Launch.command
        * Running this file will launch Genvisis on a Unix/Linux/Mac machine
    * launch.properties
Contains properties used by all Genvisis projects
Eg. Path to PLINK software, location of resources/, location of projects/, record of the last project opened, etc.
    * Launch.sh
Running this file will launch Genvisis on a Unix/Linux/Mac machine