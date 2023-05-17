# Introduction to the Workflow

Genvisis data processing is run from a workflow of steps that automate best practices. The Genvisis Workflow can be opened from the toolbar (check the *Workflow* button) or from **Data > Genvisis Project Workflow**.

<p id="gdcalert2" ><span style="color: red; font-weight: bold">>>>>>  gd2md-html alert: inline image link here (to images/image2.png). Store image on your image server and adjust path/filename/extension if necessary. </span><br>(<a href="#">Back to top</a>)(<a href="#gdcalert3">Next alert</a>)<br><span style="color: red; font-weight: bold">>>>>> </span></p>

![alt_text](images/image2.png "image_tooltip")

**Image of the Genvisis toolbar with Workflow icon highlighted**

The Workflow window lists all available steps. To run a step, check the box next to the numbered step. Each sub-step will be green or red; green text means Genvisis is ready to run this sub-step, while red text means there are missing requirements that must be addressed first. Higher-numbered steps may not be able to run without earlier steps being run first. Auto-populated file names will be green if they exist and red if they don't exist.

<p id="gdcalert3" ><span style="color: red; font-weight: bold">>>>>>  gd2md-html alert: inline image link here (to images/image3.png). Store image on your image server and adjust path/filename/extension if necessary. </span><br>(<a href="#">Back to top</a>)(<a href="#gdcalert4">Next alert</a>)<br><span style="color: red; font-weight: bold">>>>>> </span></p>

![alt_text](images/image3.png "image_tooltip")

**Image of the Genvisis Project Workflow dialog box. Green text indicates steps that are ready to be run, while red text indicates steps for which prerequisites have not been met.**

The first four steps of the workflow depend on the platform of your original data (Illumina or Affymetrix). The rest of the steps are the same regardless of platform.
