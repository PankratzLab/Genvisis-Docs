### Compute GCMODEL File

This step computes the guanine and cytosine content around a marker. Many Gs and Cs in a row means that a portion of the double helix is more tightly bound and takes more energy to separate due to G and C having 3 hydrogen bonds instead of 2 (as with A and T). Regions with many Gs and Cs have properties that are detected downstream, such as how tightly something is hybridizing to it, the degree of intensity (X and Y), and is a problem when the sample is of low quality.

This option computes the average GC content at each location and corrects for it.

This option requires a file that is relative to the genome build (eg. hg18_gc5base.txt) that should automatically download from the Genvisis website. The file downloads to **.genvisis/resources/Genome/**.
