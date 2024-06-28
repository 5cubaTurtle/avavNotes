Halt, power-off or reboot the machine


Shutdown immediately: `sudo shutdown +0`, or `now`

Reboot in 10 minutes: `shutdown -r +10`
- `-H, --halt` Halt the machine.
- `-P, --poweroff` Power-off the machine (the default).
-  `-r, --reboot` Reboot the machine.
-  `-h` Equivalent to --poweroff, unless --halt is specified.
-  `-k` Do not halt, power-off, reboot, just write wall message.
-  `--no-wall` Do not send wall message before halt, power-off, reboot.
- `-c` Cancel a pending shutdown. This may be used to cancel the effect of an invocation of shutdown with a time argument that is not "+0" or "now".

miscellaneous
