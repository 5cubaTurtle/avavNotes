---
doc: https://www.freedesktop.org/software/systemd/man/latest/index.html
wiki: https://en.wikipedia.org/wiki/Systemd
---

Systemd is a system and service manager that provides a range of functionalities for controlling and monitoring services on a Linux system.

Check if using System V or systemd: `ps --no-headers -o comm 1`

### Links
[Website](https://systemd.io/)
Manage systemd [guide](https://www.digitalocean.com/community/tutorials/how-to-use-systemctl-to-manage-systemd-services-and-units) using [[systemctl]]
### Debugging
[guide](https://containersolutions.github.io/runbooks/posts/linux/debug-systemd-service-units/)
### boot analyzing
check total boot time: `systemd-analyze`
check per service boot time: `systemd-analyze blame`
plot of the system's boot process: `systemd-analyze plot > bootchart.svg`, into *.svg* file


### /etc/systemd/
####  system/
- **Purpose**: This directory contains system-wide unit files, which define services, targets, and other systemd units. These units are used to manage services and system states.
- **Contents**: Unit files typically have extensions like `.service`, `.socket`, `.target`, etc.
    - **`.service` files**: Define services.
    - **`.socket` files**: Define socket-activated services.
    - **`.target` files**: Define target units, which group other units together.
- **Hierarchy**: This directory is used for custom unit files and overrides. Files in this directory take precedence over unit files in `/lib/systemd/system/`.
#### user/
- **Purpose**: This directory contains user-level unit files. These units are used to manage services and other systemd units that run in user mode rather than system mode.
- **Contents**: Similar to the system directory, but these units are managed by the `systemd --user` instance and are specific to individual users.
    - **`.service` files**: Define user services.
    - **`.socket` files**: Define user socket-activated services.
    - **`.target` files**: Define user targets.
- **Usage**: Allows users to manage their own services without requiring root permissions. This is useful for applications that need to start services when a user logs in.

#### network/
See [[networkd#/etc/systemd/network/]]
