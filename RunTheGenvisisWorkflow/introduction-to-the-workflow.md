# Introduction to the Workflow

Genvisis data processing is run from a workflow of steps that automate best practices. The Genvisis Workflow can be opened from the toolbar (check the *Workflow* button) or from **Data > Genvisis Project Workflow**.

![Image of the Genvisis toolbar with Workflow icon highlighted](/Images/GenvisisToolBarHighlight.png)

The Workflow window is organized into groups based on what type of analysis you wish to perform.  The six groups are:
- Explore Samples
- Detect Mosaic Chromosomal Alterations
- Impute Genotype Data to a Reference Panel
- Correct for Batch Effects
- Call Mitochondrial DNA Copy Number
- Call Copy Number Variants (CNVs) 

Checking the box for a group will display the steps required to perform that analysis.

![Image of the Genvisis Project Workflow dialog box. Green text indicates steps that are ready to be run, while red text indicates steps for which prerequisites have not been met.](/Images/WorkflowShort.png)

To run a step, check the box next to the numbered step. Each sub-step will be green or red; green text means Genvisis is ready to run this sub-step, while red text means there are missing requirements that must be addressed first. Higher-numbered steps may not be able to run without earlier steps being run first. Auto-populated file names will be green if they exist and red if they don't exist.

The first four steps of the workflow depend on the platform of your original data (Illumina or Affymetrix). The rest of the steps are the same regardless of platform.
