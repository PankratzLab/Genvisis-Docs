# Set Up Genvisis on Your System

**Mac** 
1. Download [XQuartz](https://www.xquartz.org/).
2. Restart your computer.
3. Set up ssh connections for your server. Contact your system administrator if you need assistance. (NO DETAIL BECAUSE SOME PARTS ARE SYSTEM-DEPENDENT?) (COULD HAVE ENTIRE 'SET UP SSH' DOCUMENT TO DESCRIBE STEP 3???)
4. Set up ssh config with X11 forwarding:
  -Create or modify ~/.ssh/config with the following information: (“vi ~/.ssh/config)
  -Ensure file permissions are set (“chmod 600 ~/.ssh/config”)

In your ssh config, set **XAuthoLocation** (MAYBE NOT REQUIRED???) and **ForwardX11**.
XAuthLocation /opt/X11/bin/xauth (THIS IS THE PATH FOR MAC; APPEARS TO BE NOT REQUIRED FOR LINUX.)

5. Add the following line to each host in your ssh config file:
  ForwardX11 yes
Note: X11Forwarding yes applies forwarding to ALL ssh commands. If this is too aggressive, you can also pass the “-X” flag to ssh. However, it is not sufficient to pass it in the ProxyCommand, but an alias such as gomsi=ssh -X msi should work.
Note: If you open an ssh connection without X11 forwarding, you must close this one before you can open a new terminal that does have X11 forwarding.

MAYBE CUT "on MSI"?  
Note for Apple silicon users: When running Genvisis on MSI with X11 forwarding, set this option to prevent odd rendering issues: -Dsun.java2d.xrender=false 
  -Example of the full command: java -Dsun.java2d.xrender=false -jar genvisis.jar



**Windows**
1. Download [Xming](https://xming.en.softonic.com/download) and [PuTTY](https://www.putty.org/).
2. In PuTTY, set up your ssh connection and X11 forwarding. Create a saved session with these instructions and the following settings:
  * Session > Host Name: (your host name here, e.g., mesabi.msi.umn.edu)
  * Connection>Proxy (NOT SURE IF THIS IS STILL NEEDED? ASK NATHAN)
    * Proxy hostname: login.msi.umn.edu
    * Telnet command, or local proxy command relies on having plink.exe (the TTY client, not the genetics toolset PLINK) on your path. Renaming this to plink_ssh.exe or something similar and then modifying the command to match may be advisable.
  * Connection>SSH
    * Check box for Share SSH connections if possible
  * Connection>SSH>X11
    * Ensure Enable X11 forwarding is checked

3. We recommend that you save your session as something you will remember to access next time you log in.
4. For convenience, you can set up PuTTY to Automatically Load a Session. (ADD LINK)
