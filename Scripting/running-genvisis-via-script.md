## Running Genvisis Via Script



1. Genvisis workflow steps can be run in a high performance computing environment via scripts.
2. In the lower right hand corner of the Workflow window is the button **Export to Text**.
    1. Clicking this will produce a **.toml** file that lists which Genvisis steps to run and a **.slrm** file for the SLURM (Simple Linux Utility for Resource Management) format in **[ProjectDir]/scripts/**.
    2. A pop up window will say “GenvisisWorkflow command file written to **[ProjectDir]/scripts/[toml file name]**.” The pop up window will also have a **Copy to Clipboard** button that will copy the path to the **.toml** and **.slrm** files.
3. Here is a sample **.toml** file created for the Run Marker BLAST Annotation step:

    ```
    ## Genvisis Workflow Command File
    ## Genvisis Version: 0.1.16 (interim build f4ee9bb)
    ## Created 2022.07.16 at 04:17:21PM

    [project]
    file = '/home/userName/projects/SampleProject.properties'

    [targets]

     [targets.illumina-blast]
    	manifest = '/home/SampleProject/Phase3/HumanOmniExpressExome-8-v1-1-C'
    	positionOverrides = ''
    	threads = 24
    ```


4. The associated **.slrm** file:

    ```
    #!/bin/bash
    #$ -cwd
    #$ -S /bin/bash
    #SBATCH --error=%x.%j.e
    #SBATCH --output=%x.%j.o
    #SBATCH --mail-type=END,FAIL
    #SBATCH -N 1
    #SBATCH -n 1
    #SBATCH --mem 100G
    #SBATCH --time=24:00:00
    echo "start GenvisisWorkflow.SampleProject.2022.07.16_04_17_21PM at: " `date`
    echo "host/node: " `/bin/hostname`
    cd /home/SampleProject/Phase3/
    java -Xmx90G -Djava.awt.headless=true -jar ~/genvisis.jar org.genvisis.cnv.workflow.GenvisisWorkflow "/home/SampleProject/Phase3/scripts/GenvisisWorkflow.SampleProject.2022.07.16_04_17_21PM.toml"
    echo "end GenvisisWorkflow.SampleProject.2022.07.16_04_17_21PM at: " `date`
    ```


5. SLURM settings:

    **error**: name of error file (appends timestamp and submission number to file name)


    **output**: name of log file


    **mail-type**: email the user when either the job successfully ends or fails


    **N**: number of nodes


    **n**: number of processors per node


    **mem**: memory requested


    **time**: walltime requested

6. In **java -Xmx90G -jar ~/genvisis.jar**, notice we request 90GB of RAM for Genvisis while above in **#SBATCH --mem=100gb**, we request 100GB from the node. Genvisis automatically lowers the amount of memory reserved for Java by 10% of the total memory request to provide overflow space for any meta-tasks that may need to occur beyond the specific Genvisis step. **-Xmx#** can be edited as the user sees fit relative to their environment and data needs.
7. Submit the **.slrm** file using:

    ```
    sbatch -p partionName fileName.slrm
    ```


8. If you receive the error message **script is written in DOS/Windows text format** when trying to submit the job (due to generating the .slrm file on a PC and then moving it to an HPC environment), you’ll need to convert the file with **dos2unix**:

    ```
    dos2unix [fileName].slrm
    ```


9. After submitting your job, you can check on its progress with **squeue -u [userName]** or **squeue -a --me**. Potential status (**ST**) codes are:

    CD - Completed; The job has completed successfully.


    CG - Completing; The job is finishing but some processes are still active.


    F - Failed; The job terminated with a non-zero exit code and failed to execute.


    PD - Pending; The job is waiting for resource allocation. It will eventually run.


    PR - Preempted; The job was terminated because of preemption by another job.


    R - Running; The job currently is allocated to a node and is running.


    S - Suspended; A running job has been stopped with its cores released to other jobs.


    ST - Stopped; A running job has been stopped with its cores retained.

10. To cancel a job, use **scancel [jobIdNumber]**
