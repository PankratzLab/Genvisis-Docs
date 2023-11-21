# CompPlot

CompPlot visualizes all deletions (shown in a darker shade) and duplications (lighter shade) within a particular region of the genome for an entire study population at once. If we see many events overlapping a particular gene in individuals with a particular disease (red colors) and relatively few in healthy individuals (green color), then that gene is a likely cause of the disease.

CompPlot displays CNV calls per chromosome. The text box in the top center of the window displays the chromosome and position being displayed. Clic on the arrow buttons to view a different chromosome. Use your mouse scroll wheel to adjust the zoom. Click and drag the screen to move left or right on the chromosome.

The length of each bar corresponds to the length of the call (in base pairs).

On the right is the **Display Mode** option. **Full** shows one sample per line. **Pack** removes the vertical space between calls so that multiple samples can be in the same row. A new row is used only when call share the same positions. **Collapsed** combines calls that are the same size and displays a number on the left end of the bar to indicate how many calls are that length at that location.

Place the cursor over a call to see information about it. Calls can be opened in TrailerPlot either by clicking on an individual call and choosing **To Trailer: Selected**, or by selecting **To Trailer: Visible** to load all calls on the screen.

Multiple CNV call lists can be displayed simultaneously. For example, for a given set of samples, you might want to compare calls made by a different method and calls produced by Genvisis. Genvisis stores CNV calls in **[ProjectDir]/cnvs/genvisis.cnv**. The calls that CompPlot uses are listed in the **Project Properties Editor** on the main toolbar. In **Project Properties**, scroll to the **CNV Files** header. There will be a field called **CNV_FILENAMES**. Click **+** to add additional **.cnv** files. Then click **Save and Close**. If the new CNV calls do not show up in CompPlot, it might be necessary to close and relaunch Genvisis.
