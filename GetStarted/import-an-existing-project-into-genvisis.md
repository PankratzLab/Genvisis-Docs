# Import an Existing Project

If you have a pre-existing Genvisis project that was created by a different user, you can import that project into your 
local environment as follows:

1. On the [Menu Bar](../#/documentation/menu), go to **File** → **Import Project**.
2. The **Genvisis Project Import** pop-up window will appear. There will be a list of requirements each with a red X next to them.
3. Click **…** next to **Project Directory**.
4. Choose the directory of the existing project and click **Select**
5. **New Project Name** will now contain the name of the project. 
6. The red X for each requirement will turn into a green checkmark if the file or directory is present.  If the requirement is missing, the project can still be created, but Genvisis features that rely on it will not work. You will need to rerun the relevant [Workflow](../#/documentation/RunTheGenvisisWorkflow--introduction-to-the-workflow) steps to regenerate the missing file or directory.
7. Click **OK**.  This will create a properties file in your [resources directory](../#/documentation/resources-directory)  based on the data in the project's [ProjectDir]/data/import.ser file.
8. The imported project will load in Genvisis and can now be used.
