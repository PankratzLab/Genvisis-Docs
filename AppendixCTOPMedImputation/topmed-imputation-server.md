# TOPMed Imputation Server
1. Go to the [TOPMed Imputation Server](https://imputation.biodatacatalyst.nhlbi.nih.gov/#!) and sign up for an account
2. Click Run -> Genotype Imputation (Minimac4) at the top of the page
3. You’ll be taken to the submission page:

        **Name**

        An optional name for your submission

        **Reference Panel**

        The only option on the public server is TOPMed r2, which consists of 194,512 haplotypes from 97,256 samples.
        [https://topmedimpute.readthedocs.io/en/latest/reference-panels/](https://topmedimpute.readthedocs.io/en/latest/reference-panels/)

        **Input Files (VCF)**

        Files sent to the TOPMed server must be .vcf. You can upload them from a local machine, point to an HTTP address, an SFTP address, or an Amazon S3 Bucket. Genvisis produces index (.vcf.gz.tbi) files along with the .vcf, but only the .vcf are needed. Only chromosomes 1-22 and X can be imputed. Don’t submit Y, XY, MT, or Unknown as they will cause the quality check to fail. And it won’t tell you why it failed.

        **Array Build**

        The project must be in either **GRCh37/hg19** or **GRCh38/hg38**

        **rsq Filter**

        To minimize the file size, Michigan Imputation Server includes an r2 filter option, excluding all imputed SNPs with an r2-value (= imputation quality) smaller than the specified value. We will filter on r2 ourselves after the fact, so select **off** for this.

        **Phasing**

        Our data is unphased, so select the Eagle v2.4 (phased output) option to phase the data during processing. Phased data identifies which chromosome of each pair is the source of the genome.

        **Population**

        Run the **TOPMed r2 vs. TOPMed Panel** option (the only time this QC check is not relevant is if you have a very specific non-European population).

        **Mode**

        Choose **Quality Control & Imputation.**

        **AES 256 encryption**

        The imputation files produced will always be encrypted, but you have the choice to add an extra layer of security to your data by using Advanced Encryption Standard with a key length of 256 bits. This isn’t necessary if your data isn’t Protected Health Information (PHI).

        **Generate Meta-imputation file**

        A checkbox to produce meta-data about the imputation results.

4. Finally, check the boxes agreeing to protect research participant privacy.
5. After the job completes, you’ll receive an email with a password and a link to a webpage with links for the files that were created.
They include Quality-Control Report, QC Statistics, Imputation Results, and Logs.
Click the wget button in the upper right corner of each section and it will provide you with commands you can paste into the linux command line to download the files to MSI.
The files that download will be zipped, but require the password in the email to unzip. Download all of the imputation files to a dir on MSI, and then inside the dir run:
unzip -P [password] “*.zip” -d [dir to place unzipped files in]
6. Imputation files can then be used with the Genvisis module Gene Score Pipeline.

