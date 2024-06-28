[tutorial](https://www.digitalocean.com/community/tutorials/understanding-systemd-units-and-unit-files)
[[systemd]] service units are configuration files that define how a service should be managed by the systemd init system in Linux. These are ini-style files.

## Sections
Common sections in unit file:
1.  [¶](https://www.freedesktop.org/software/systemd/man/latest/systemd.unit.html) `[Unit]` Provides common options of all unit configuration files. It includes options like `Description`, `Requires`, `After`, `Before`, `Conflicts`, `PartOf`, and `Wants`.
	- `Description`: A description of the service.
	- `After`: Specifies service dependencies, ensuring that service starts after these targets.
1.  [¶](https://www.freedesktop.org/software/systemd/man/latest/systemd.service.html) `[Service]` Defines how the service should be started, stopped, and managed. It includes options like `ExecStart`, `ExecStop`, `User`, `Group`, `Restart`, `TimeoutSec`, `Type`, `PIDFile`, and `Environment`.
2.  `[Install]` Defines how the unit should be installed and started during system boot. Like [Unit] this section contains common options of all unit configuration files. It includes options like `WantedBy`, `RequiredBy`, `Alias`, and `Also`.
3.  [¶](https://www.freedesktop.org/software/systemd/man/latest/systemd.socket.html) `[Socket]` Defines a socket unit file, which is used to listen for incoming network connections or file system events.
4.  [¶](https://www.freedesktop.org/software/systemd/man/latest/systemd.device.html)`[Device]` Defines a device unit file, which is used to manage a device file in the file system.
5.  [¶](https://www.freedesktop.org/software/systemd/man/latest/systemd.mount.html)  `[Mount]` Defines a mount unit file, which is used to manage file system mounts.
6.  [¶](https://www.freedesktop.org/software/systemd/man/latest/systemd.automount.html)`[Automount]` Defines an automount unit file, which is used to automatically mount file systems on demand.
7.  [¶](https://www.freedesktop.org/software/systemd/man/latest/systemd.target.html)`[Target]` Defines a target unit file, which is used to group and order other units during system boot.

### Service
The "Service" section contains [directives]() that define how the service should be executed and managed by systemd. Here are some commonly used directives found in the "Service" section:
1. **Type**: Specifies the process type of the service. Possible values include `simple` (default), `forking`, `oneshot`, `dbus`, and `notify`. The default `simple` type assumes that the process started by the service remains the main process until the service is stopped.
2. **ExecStart**: Defines the command or script to start the service. It can include the full path to an executable, along with any command-line arguments.
3. **ExecStartPre**, **ExecStopPost**: Specifies additional commands or scripts to be executed before or after the main `ExecStart` command.
4. **ExecReload**: Defines the command or script to reload the service configuration. It is used when the service supports reloading without a full restart.
5. **ExecStop**: Specifies the command or script to stop the service. This is used when the service needs explicit termination rather than relying on a signal.
6. [[Restart]]: Determines the conditions under which the service should be automatically restarted. Possible values include `no` (default), `always`, `on-success`, `on-failure`, `on-abnormal`, `on-abort`, and `on-watchdog`.
7. **RestartSec**: Defines the time duration in seconds that systemd should wait before attempting to restart the service again.
8. **User** and **Group**: Specifies the user and group under which the service should run. This helps in providing security and resource isolation.
9. **WorkingDirectory**: Sets the working directory for the service process.
10. **Environment**: Defining environment variables for the service.
11. [[EnvironmentFile]]: Specifies one or more files from which systemd should read environment variable assignments for the service. `Environment` directive takes precedence over `EnvironmentFile`.
12. **StandardOutput** and **StandardError**: Determines where the service's standard output and standard error should be logged. Possible values include `inherit`, `null`, `journal`, `syslog`, or a file path.

There are additional directives available for controlling resource limits, file system mounts, dependencies, timers, and more. The specific directives and their options may vary depending on the version of systemd and the Linux distribution you are using. You can refer to the systemd documentation.

### Example:
```ini
[Unit]
Description=WPA supplicant
Before=network.target
After=dbus.service
Wants=network.target
IgnoreOnIsolate=true

[Service]
Type=dbus
BusName=fi.w1.wpa_supplicant1
ExecStart=/sbin/wpa_supplicant -u -s -O /run/wpa_supplicant

[Install]
WantedBy=multi-user.target
Alias=dbus-fi.w1.wpa_supplicant1.service
```
