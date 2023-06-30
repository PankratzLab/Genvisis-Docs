# Exclude Samples (optional)

Rationale: If you only want to export a subset of samples, or if you want to cluster on a set of high-quality samples (independent of the call rate >0.98 recommended above), then you can import a file that delineates which samples you want.
In the Samples Table in the lower left hand corner, the fifth icon is called Import columns into the table. Click it and the Import pop-up window will appear. Keep the Column Import option checked. Click Browse… next to the Tab-delimited text file to import text field. Choose ExcludedSamples.xln or an ExcludesUsing… file, and then hit OK in the Import window.
Note: The .xln file may not appear if the only option for files is .txt. You can enter *.* in the File name field and hit Enter to make it show up.
The Exclude column from excludes file will appear in the Samples Table. You can now sort by this to cluster on only high quality samples and/or if you want to export only certain samples in the FinalReport files.
