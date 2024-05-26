[manage systemd](https://www.digitalocean.com/community/tutorials/how-to-use-systemctl-to-manage-systemd-services-and-units) using [[systemctl]]

Check if using System V or [[systemd]]: `ps --no-headers -o comm 1`

Systemd is a system and service manager that provides a range of functionalities for controlling and monitoring services on a Linux system.

#### Debugging
[guide](https://containersolutions.github.io/runbooks/posts/linux/debug-systemd-service-units/)
Printing to [[journalctl|journal]] we need flush the buffer after calling the [[print()]] statements. To do that use the [[sys]] package: 

#### boot analyzing
check total boot time: `systemd-analyze`
check per service boot time: `systemd-analyze blame`
plot of the system's boot process: `systemd-analyze plot > bootchart.svg`, into *.svg* file
