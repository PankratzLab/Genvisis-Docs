# Exclude Samples (optional)

If you want to export only a subset of your samples, or if you want to cluster on a set of high-quality samples (independent of the call rate >0.98 recommended above), then you can import a file that delineates which samples you want.

1. In the Samples Table in the lower-left corner, click **Import columns into the table**. You will see the **Import** pop-up window.
2. Keep the **Column Import** option checked. 
3. Click **Browse…** next to the tab-delimited text file to import text field. 
4. Choose **ExcludedSamples.xln** or an **ExcludesUsing…** file, and then click **OK**. (Note that the **.xln** file may not appear if the only option for files is **.txt**. You can enter *.* in the file name field and click **Enter** to force it to appear.)
5. The Exclude column from excludes file will appear in the Samples Table. You can now sort by this file to cluster on only high quality samples and/or if you want to export only certain samples in the FinalReport files.
