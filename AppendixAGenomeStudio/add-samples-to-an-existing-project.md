# Add Samples to an Existing Project

1. Go to *File > Load Additional Samples…*. A project wizard will pop up.
    * By default, the **.idat** files that are loaded will use Sentrix ID and Position for Sample ID. If this is appropriate, choose **Load sample intensities by selecting directories with intensity files** and follow the instructions for creating a new project.
    * If you want to use alternative IDs, such as IDs provided by the lab that created the **.idat** files came, select **Use sample sheet to load sample intensities**.
      * [Here is an example sample sheet](https://github.com/PankratzLab/Genvisis-Docs/blob/main/AppendixAGenomeStudio/GenomeStudio_Sample_Sheet.csv) (external link).
      * Tip: If you receive an error message that the manifest in the sample sheet does not match the manifest loaded in the existing project, delete the manifest name from the sample sheet (row #8 in the above example file). (Using the same manifest name in the sample sheet as that in the existing project has caused this error to occur in the past. GenomeStudio will import files with no manifest in the sample sheet, however.)
      * Tip: If you created a sample sheet using Excel, open it in Notepad or Textpad to verify there are no blank rows after the final sample. GenomeStudio will create a sample list with more samples than idat files if the sample sheet contains blank rows.
    * The imported samples won’t have **Call Rate**. You’ll need to highlight all the new samples, right click on them, and select **Recalculate Statistics for Selected Samples**.
    * Also note the **Rows** and **Disp** values below the samples. The number of rows will match the total number of samples in the project. If **Disp** is smaller, not every sample is appearing in the **Samples Table**. To correct this issue, go to the **Samples Table** toolbar (you might have to click the drop-down arrow for more options) and click **Clear filter**.
      * Tip: There have been situations in the past where samples were not displayed, but the statement **Filter=Filter is not active** was present below the table. **Clear filter** displayed the samples despite no filter being active.
