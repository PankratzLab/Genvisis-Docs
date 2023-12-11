# Set Up X11 Forwarding 

If you will be running Genvisis on a remote Linux system, you need to set up X11 forwarding on your machine.

## Mac 
1. Download [XQuartz](https://www.xquartz.org/).
2. Restart your computer.
3. Set up your ssh config file with X11 forwarding:
   - Create or modify ~/.ssh/config as follows: vi ~/.ssh/config
   - Ensure file permissions are set: chmod 600 ~/.ssh/config
4. Add the following line to each host in your ssh config file (not to the general **Host** section): ForwardX11 yes

Example file (note that the Host * section might be different on your system or might not be required):

   ```
Host *
      ControlMaster auto
      ControlPath /tmp/%r@%h:%p
      ControlPersist 12h
        
Host yourShortcutHere
        HostName yourhostname.example.edu
        User exampleuser001
        IdentityFile ~/.ssh/youridentityfilename
        ForwardX11 yes
   ```

Note: **ForwardX11 yes** applies forwarding to *all* ssh commands. If you think this is too aggressive, you can also pass the “-X” flag to ssh. It is not sufficient to pass it in the ProxyCommand, but an alias such as **[my shortcut]=ssh -X [server name]** should work.

Note: If you open an ssh connection without X11 forwarding, you must close it before you can open a new terminal that does have X11 forwarding.

Note for Apple silicon users: When running Genvisis with X11 forwarding on your server, set the following option to prevent odd rendering issues: **-Dsun.java2d.xrender=false**. For example, the full command might be **java -Dsun.java2d.xrender=false -jar genvisis.jar**.


## Windows
1. Download [Xming](https://xming.en.softonic.com/download) and [PuTTY](https://www.putty.org/).
2. In PuTTY, set up your ssh connection and X11 forwarding. Create a saved session with the following settings:
   - Session > Host Name: [your host name here, e.g., mesabi.msi.umn.edu]
   - Connection > Proxy (not necessary on all systems)
      - Proxy hostname: [your login node, if you have one]
      - Telnet command, or local proxy command relies on having plink.exe (the TTY client, not the genetics toolset PLINK) on your path. Renaming this plink_ssh.exe or something similar and then modifying the command to match may be advisable.
   - Connection > SSH
      - Check box for **Share SSH connections** if possible
   - Connection > SSH > X11
      - Ensure **Enable X11 forwarding** is checked
3. We recommend that you save your session as something you will remember to access next time you log in.
4. For convenience, you can set up PuTTY to [automatically load a saved session](https://documentation.help/PuTTY/using-cmdline-load.html).
