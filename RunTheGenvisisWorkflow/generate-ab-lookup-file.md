## Generate AB Lookup File

This step parses the AB alleles from the original genotype. For each of the variants, it matches what nucleotide it predicts the A allele is and what nucleotide the B allele is to determine what is the reference allele and what is the alternate allele.

Requires **Parse Sample Files** to have been run.

Will use **Marker BLAST Annotations** if they are available. If Genvisis was unable to run the Run Marker BLAST Annotation step (because no file containing probe sequences was available) then this step will take longer than usual. Typically the Generate AB Lookup File step is very fast; if the marker BLAST annotations are unavailable the Generate AB Lookup File step will take much longer to run because Genvisis must determine the AB alleles from the clusters instead of the BLAST annotation file.

Has the option to take the **SNP\_Map.csv** file that GenomeStudio creates with the report files. **SNP\_Map.csv** is used only in the rare scenario where you have neither probe sequences nor a blast.vcf file. When Genvisis generates a lookup from existing ACGT genotypes and then reclusters a monomorphic marker, the only way to determine the other allele is with **SNP\_Map.csv** or a similar file.
