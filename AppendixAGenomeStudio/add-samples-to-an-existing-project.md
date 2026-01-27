# Add Samples to an Existing Project

To add samples, go to *File > Load Additional Samples…*. A project wizard will pop up.

By default, the **.idat** files that are loaded will use Sentrix ID and Position for Sample ID. If this is appropriate, choose **Load sample intensities by selecting directories with intensity files** and follow the instructions for creating a new project. If you want to use alternative IDs, such as IDs provided by the lab that created the **.idat** files, select **Use sample sheet to load sample intensities**.

[Here is an example sample sheet](https://github.com/PankratzLab/Genvisis-Docs/blob/main/AppendixAGenomeStudio/GenomeStudio_Sample_Sheet.csv) (external link).

Tip: Make sure that the Sample_ID or Sample_Name (whichever you merge into GenomeStudio) is unique. For example, if you have duplicate samples named NA12878, rename them something like NA12878_1 and NA12878_2. If you leave two samples named NA12878, Genvisis will automatically rename the first one it sees NA12878_1 and the second one it sees NA12878_2; however, you will have lost the provenance back to the SENTRIX_ID and to the idat files used to generate the data. It is therefore better to rename duplicate samples yourself so that you can compare analyses from other pipelines (e.g., MoChA).

Tip: It is possible to import multiple studies into the same Genvisis project if they have the same set of markers, for instance, different genotyping batches that have been clustered separately in different GenomeStudio projects. We strongly advise against doing so, since it can lead to significant batch effects that can bias your final results; however, this practice is unavoidable if your batches were genotyped on different versions of the same array (e.g., HumanCoreExome-12v1-1_B, InfiniumCoreExome-24v1-1_A, and InfiniumCoreExome-24v1-3_A1). If you import multiple studies into the same Genvisis project, you should export/import the data for only those markers that are present on all arrays and you should ensure that each Sample_ID/Sample_Name is unique across studies as well as within each study.

Tip: If you receive an error message that the manifest in the sample sheet does not match the manifest in the existing project, delete the manifest name from the sample sheet (row #8 in the above example file). (Using the same manifest name in the sample sheet as that in the existing project has caused this error to occur in the past. GenomeStudio will import files with no manifest in the sample sheet, however.)

Tip: If you created a sample sheet using Excel, open it in a program such as Notepad or Textpad to verify that there are no blank rows after the final sample. GenomeStudio will create a sample list with more samples than **.idat** files if the sample sheet contains blank rows.

The imported samples will not have **Call Rate**. Highlight all the new samples, right click on them, and select **Recalculate Statistics for Selected Samples**.

Note the **Rows** and **Disp** values below the samples. The number of rows will match the total number of samples in the project. If **Disp** is smaller, not every sample is appearing in the **Samples Table**. To correct this issue, go to the **Samples Table** toolbar (you might have to click the drop-down arrow for more options) and click **Clear filter**.

Tip: We have seen situations in which samples were not displayed but **Filter=Filter is not active** was present below the table. Selecting **Clear filter** displayed the samples despite no filter being active.
