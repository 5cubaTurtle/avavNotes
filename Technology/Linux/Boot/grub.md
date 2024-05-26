Grand Unified Bootloader

[Article](https://www.makeuseof.com/what-is-grub/)
GRUB is mainly responsible for providing you with an options menu from which you can select the operating system or environment that you want to boot into. In addition, GRUB is responsible for loading [the Linux Kernel](https://www.makeuseof.com/tag/what-is-kernel-in-linux-check-version/). Could also boot [[windows]]
### [Accessing grub menu](https://askubuntu.com/a/16049)
Keep pressing once a second the `Esc`.

### Configure grub to appear at boot
info: `info -f grub -n 'Simple configuration'`

You'll need to edit your `/etc/default/grub` file:

- Comment the line: `# GRUB_TIMEOUT_STYLE=hidden`, this will cause to resort to the default setting: `GRUB_TIMEOUT_STYLE=menu`.
- Then change `GRUB_TIMEOUT=0` to `GRUB_TIMEOUT=5`, for instance, to give the grub menu a 5 second timeout before it automatically logs you in.
- Save changes and run `sudo update-grub` to apply changes.

Documentation: [https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)