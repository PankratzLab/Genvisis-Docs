# Add Samples to an Existing Project

1. File > Load Additional Samples…
2. A project wizard will pop up
    * The .idat files that are loaded will default to using Sentrix ID and Position for Sample ID. If this is ok, choose Load sample intensities by selecting directories with intensity files and follow the instructions for creating a new project.
    * If you want to use alternative IDs for samples, such as IDs provided by the lab the .idats came from, select Use sample sheet to load sample intensities.
      * Example sample sheet
      * Tip: If you receive an error message that the manifest in the sample sheet doesn’t match the manifest loaded in the existing project, delete the manifest name from the sample sheet (row #8 in the above example file; using the same manifest name in the sample sheet as that in the existing project has still caused this error to occur in the past. GenomeStudio will import files with no manifest in the sample sheet, however).
      * Tip: If you created a sample sheet using Excel, open it in Notepad or Textpad and verify there aren’t blank rows after the final sample. GenomeStudio will create a sample list with more samples than idats if the sample sheet has blank rows.
    * The imported samples won’t have Call Rate. You’ll need to highlight all the new samples, right click on them > Recalculate Statistics for Selected Samples
    * Also take note of the Rows and Disp values below the samples. The number of rows will match the total number of samples in the project, but if Disp is smaller, not every sample is appearing in the Samples Table. To correct this, click Clear filter on the Samples Table toolbar (you might have to click the drop down arrow for more options).
      * Tip: There have been situations in the past where samples were not displayed, but the statement Filter=Filter is not active was present below the table. Clear filter displayed the samples despite no filter being active.
