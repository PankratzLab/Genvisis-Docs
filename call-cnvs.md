### Call CNVs

Part 1.1 takes an .hmm file, which contains the parameters for a Hidden Markov Model
* The model parameters are stored in **.genvisis/resources/CNV/hhall.hmm**, which Genvisis automatically downloads.
* **hhall.hmm** is Genvisis’s default model. There is also **hh550.hmm**, which is for the Illumina 550 array. The PennCNV algorithm was originally written for the 550 array.
* Genvisis uses the same CNV calling algorithm as PennCNV.
* The HM model looks for change states; a change in intensity may indicate a deletion or a duplication.
* In the **hhall.hmm** file are mean and standard deviation values that indicate the number of copies of an allele.
* B1 is for the log R ratio and B2 is for the B allele frequency.
* Values were derived empirically from an array
  * -3.5	-0.66	0	100	0.4	0.68
  * The six values are for copy number 0 (homozygous deletion), 1, 2 heterozygous, 2 homozygous, 3 (duplication), and 4 (triplication)
  * Copy number 2 homozygous is turned off by being set to 100 because values that high will never be seen. hh550.hmm has homozygous set to 0.0.
* The .hmm file created in **Step 21: Process CNVs and Create HMM File**, can also be used here to call CNVs a second time with an .hmm file customized to the dataset (the **Create HMM File** step also has an option to recall CNVs automatically).

Part 4: CNV Calling Scope (three options)
* **BOTH (default):** Calls **AUTOSOMAL** and **SEX CHROMOSOMES** 
* **AUTOSOMAL:** Chromosomes 1 to 22
* **SEX CHROMOSOMES:** Chromosomes 23 (X) and 24 (Y)
