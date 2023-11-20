# Set Up Genvisis on Your System

**Mac** 

1. Download [XQuartz](https://www.xquartz.org/).
2. Restart your computer.
3. Do ____ to enable X11 forwarding.

**Windows**

1. Download Xming and PuTTY.
2. In PuTTY, set up a saved session with these instructions and the following settings:
Session > Host Name: mesabi.msi.umn.edu
-Connection>Proxy
Proxy hostname: login.msi.umn.edu
Telnet command, or local proxy command  relies on having plink.exe (the TTY client, not the genetics PLINK) on your path. Renaming this to plink_ssh.exe or something of the sort and then modifying the command to match may be advisable.
Connection>SSH
Check box for Share SSH connections if possible
Connection>SSH>X11
Ensure Enable X11 forwarding is checked
Save session as a Mesabi or something you will remember to access next time you login.
Make puTTY Automatically Load a Session

6.
7. Once the directories are set up and the necessary files are in place, run **genvisis.jar**.
    * Linux/Mac
        * Open a terminal and run **java -Xmx#g -jar [path]/genvisis.jar**
         * **#g** is the number of gigabytes of memory to use
         * [path] is the location of the genvisis.jar file
         * Example
             * **java -Xmx24g -jar ~/genvisis.jar** (if **genvisis.jar** is saved in your home directory)
        * Alternatively, locate **genvisis.jar** within a file manager and double-click on the Genvisis icon
    * Windows
        * Open a text file and write inside **java -Xmx#g -jar genvisis.jar**
        * **#g** is the number of gigabytes of memory to use
        * Example
            * **java -Xmx24g -jar genvisis.jar**
        * Save the text file as **vis.bat** in the same directory as **genvisis.jar**
        * Double-click **vis.bat**

![Image of Genvisis opened for the first time](/Images/GenvisisOpened.png)

Now you are ready to create a new project or open an existing project in Genvisis.
