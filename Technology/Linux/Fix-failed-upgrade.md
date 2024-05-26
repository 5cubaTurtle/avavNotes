[🦮](https://koen.vervloesem.eu/blog/fixing-a-failed-upgrade-to-ubuntu-2204-lts-in-recovery-mode/)
First reboot your computer and start Ubuntu in [recovery mode](https://wiki.ubuntu.com/RecoveryMode):
> If using dual-boot then just use the UEFI menu to select the Ubuntu recovery mode
- Hold the Shift key while booting the PC.
- In the GRUB boot menu that appears, choose the advanced options and then recovery mode.
- In the recovery menu that appears, enable networking first and then choose the option to open a root shell.

Because the installation has been aborted try fixing a broken install:
`apt --fix-broken install`

