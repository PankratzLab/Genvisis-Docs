# Set Up Genvisis on Your System

**Mac** 
1. Download [XQuartz](https://www.xquartz.org/).
2. Restart your computer.
3. Set up ssh connections. Contact your system administrator if you need assistance. (NO DETAIL BECAUSE SOME PARTS ARE SYSTEM-DEPENDENT?)

4. Set up ssh config with X11 forwarding.

create or modify ~/.ssh/config with the following information: (“vi ~/.ssh/config) and ensure file permissions are set (“chmod 600 ~/.ssh/config”)

In your ssh config, set **XAuthoLocation** (VERIFY THAT THIS ONE IS REQUIRED) and **ForwardX11**.

XAuthLocation /opt/X11/bin/xauth (THIS IS THE PATH FOR MAC; FIND THE PATH FOR LINUX--MAYBE THE SAME?--ASK JAMES. OR IS THIS EVEN NEEDED FOR LINUX USERS?)
ForwardX11 yes

Note: X11Forwarding yes applies forwarding to ALL ssh commands. If this is too aggressive, you can also pass the “-X” flag to ssh. However, it is not sufficient to pass it in the ProxyCommand.. but an alias like gomsi=ssh -X msi should work.

MAYBE CUT "on MSI"?  
Note for Apple silicon users: when running Genvisis on MSI with X11 forwarding, set this option to prevent weird rendering issues: -Dsun.java2d.xrender=false (example full command: java -Dsun.java2d.xrender=false -jar genvisis.jar)

(COULD HAVE ENTIRE 'SET UP SSH' DOCUMENT TO DESCRIBE STEP 3???)




**Windows**
1. Download Xming and PuTTY.
2. In PuTTY, set up your ssh connection and X11 forwarding. Create a saved session with these instructions and the following settings:
Session > Host Name: (your host name here, e.g., mesabi.msi.umn.edu)
-Connection>Proxy (NOT SURE IF THIS IS STILL NEEDED? ASK NATHAN)
Proxy hostname: login.msi.umn.edu
Telnet command, or local proxy command  relies on having plink.exe (the TTY client, not the genetics PLINK) on your path. Renaming this to plink_ssh.exe or something of the sort and then modifying the command to match may be advisable.
Connection>SSH
Check box for Share SSH connections if possible
Connection>SSH>X11
Ensure Enable X11 forwarding is checked
We recommend that you save session as something you will remember to access next time you login. 
For convenience, you can set up puTTY to Automatically Load a Session. (ADD LINK)





