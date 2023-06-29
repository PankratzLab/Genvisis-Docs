# Finding Illumina Manifest Files

GenomeStudio projects use manifest files in the form of a .bpm file. However, a .csv version of a manifest with probe sequences is needed for the first step of Genvisis when creating marker positions. If you only have the .bpm version of a manifest, you can convert it to .csv in a Linux environment with Genotype Library and Utilities:
glu-1.0b3-prerelease4-Linux_x86-64/glu convert.dump_bpm manifest.bpm -o manifest.csv

Check that the new .csv manifest contains probe sequences. These are found in the columns named AlleleA_ProbeSeq and AlleleB_ProbeSeq. The A probe must have ACGT sequences in every row to be useful. The B probe is usually null for most rows, which is fine.

If the .csv file does not contain probe sequences, you’ll need to obtain an array from the Illumina website. They maintain a list of product files here. Scroll to the bottom of the page and click Load All, and then search the page for the relevant manifest.

For example, we have the manifest GSA-24v2-0_A2.bpm included with a GenomeStudio project we receive from a wet lab. On the Illumina downloads page, there is a section for the Infinium Global Screening Array v2.0 Product Files. It has .bpm and .csv manifests for GRCh37 and GRCh38. Our SNP_Map.csv file (that GenomeStudio produced along with its final reports) uses positions from GRCh38, so we choose that .csv manifest and verify that the name of the file is identical to the .bpm we have: GSA-24v2-0_A2.csv.

Unfortunately, Illumina uses ftp to transmit the files, and web browsers have stopped supporting ftp. When you click on the link for the file, a new tab will open with a blank webpage. To get around this, copy the ftp link from the address bar and use it with wget in a Linux environment:
wget ftp://webdata:webdata@ussd-ftp.illumina.com/Downloads/ProductFiles/HumanOmniExpressExome/v1-1/HumanOmniExpressExome-8-v1-1-C.csv
