[SO](https://askubuntu.com/q/4408)
While holding `Alt` and the `SysReq (Print Screen)` (use laptop's **own** keyboard) keys, type `R` `E` `I` `S` `U` `B`.
```
R:  Switch to XLATE mode
E:  Send Terminate signal to all processes except for init
I:  Send Kill signal to all processes except for init
S:  Sync all mounted file-systems
U:  Remount file-systems as read-only
B:  Reboot
```
Some mnemonics for REISUB:

-   Rise up (from the dead) if you're inclined to zombie movies
-   **BUSIER** backwards, as in _The System is **busier** than it should be!_
-   **R**eboot **E**ven **I**f **S**ystem **U**tterly **B**roken.
-   Or the classic: **R**aising **E**lephants **I**s **S**o **U**tterly **B**oring

>There exists less radical way than rebooting the whole system. If **SysReq** key works, you can kill processes one-by-one using **Alt**+**SysReq**+**F**. Kernel will kill the most «expensive» process each time. If you want to kill all processes for one console, you can issue **Alt**+**SysReq**+**K**.

If the mouse and keyboard is responsive could also do **Alt**+**F2** to run any command like [[xkill]] or `sudo service lightdm restart`
