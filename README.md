# X11 Forwarding in VS Code and Termius
Follow the steps given below to enable the X11 forwarding in VS Code or Termius terminals for SSH connections.

**STEP 1:**
Make sure you have the following tools installed beforehand
- Xming
- SSH client 
    * To ceck the version of the SSH, type `ssh -V` in windows powershell.
     
    ```powershell
        PS C:\Users\$USER> ssh -V
        OpenSSH_for_Windows_8.1p1, LibreSSL 3.0.2
    ```
    * Upgrade the SSH client if necessary from [here](https://github.com/PowerShell/Win32-OpenSSH/releases).

**STEP 2:**
To set the DISPLAY environment variable in windows
- In powershell, use command `$env:DISPLAY="127.0.0.1:0.0"`
- To check the DISPLAY environment variable typw  `echo $env:DISPLAY`
    ```powershell 
        PS C:\Users\$USER> echo $env:DISPLAY
        127.0.0.1:0.0
    ```
- To add DISPLAY environment variable permanently, use `setx DISPLAY "127.0.0.1:0.0"`, which should technically give you this output
    ```powershell
        PS C:\Users\$USER> setx DISPLAY "127.0.0.1:0.0"

        SUCCESS: Specified value was saved.
    ```
**STEP 3:**
Login to you remote SSH server from VS code

- Edit your config file in the .ssh folder should look like this
    ```config
        Host <nick_name>
        HostName <server_address>
        User <your_user_id>
        ForwardAgent yes
        ForwardX11 yes
        ForwardX11Trusted yes
    ```
Edit your config files accordingly

- If you are using termius, login to your remote SSH like one do from any other terminal from the powersehll terminal.

<small>*NOTE*: *If you login from declared hosts in termius the X11 forwarding will not work. To me the main reason to use the termius over other terminal is the interface and the options termius offers over other terminal (it's just the choice)* </small>

**STEP 4:**
Now, just open any GUI or type any one of these `xeyes`, `xclock` and `xcalc`. You must see the display window ( make sure Xming is running). 



