# Comp Plot

CompPlot visualizes all deletions (shown in a darker shade) and duplications (lighter shade) within a particular region of the genome for an entire study population at once. If we see lots of events overlapping a particular gene in individuals with a particular disease (red colors) and relatively few in healthy individuals (green color), then that gene is likely a cause of the disease.

Displays CNV calls per chromosome. The chromosome and position on it currently displayed are described in the text box in the top center of the window. The chromosome being viewed can be changed with the arrow buttons. Zoom in and out with a mouse scroll wheel. Click and drag the screen to move left or right on the chromosome.

The lengths of the bars correspond to the lengths of the calls in basepairs.

On the right is the option **Display Mode**. **Full** shows one sample per line. **Pack** removes the vertical space between calls, so multiple samples can be in the same row. A new row is only used when call share the same positions. **Collapsed** combines calls that are the same size and displays a number on the left end of the bar for how many calls are that length at that location.

Place the cursor over a call to get information about it. Calls can be opened in Trailer Plot either by clicking on an individual call and choosing **To Trailer: Selected** on the right, or **To Trailer: Visible** to load all calls on screen.

Multiple CNV call lists can be loaded and displayed at the same time. For example, you might have calls made by a different method on the same samples and want to compare them to what Genvisis produced. Genvisis stores cnv calls in **[ProjectDir]/cnvs/genvisis.cnv**. The calls that Comp Plot uses are listed in the **Project Properties Editor** on the main toolbar. In **Project Properties**, scroll down to the **CNV Files** header and there will be a field called **CNV_FILENAMES**. Click + next to it to add additional .cnv files. Then click **Save and Close**. If the new cnv calls do not show up in Comp Plot, it might be necessary to close and relaunch Genvisis.