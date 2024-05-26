[tutorial](https://www.digitalocean.com/community/tutorials/understanding-systemd-units-and-unit-files)
[[systemd]] service units are configuration files that define how a service should be managed by the systemd init system in Linux.

## Sections
Common sections in unit file:
1.  `[Unit]` Provides a general description and configuration of the unit. It includes options like `Description`, `Requires`, `After`, `Before`, `Conflicts`, `PartOf`, and `Wants`.
2.  `[Service]` Defines how the service should be started, stopped, and managed. It includes options like `ExecStart`, `ExecStop`, `User`, `Group`, `Restart`, `TimeoutSec`, `Type`, `PIDFile`, and `Environment`.
3.  `[Install]` Defines how the unit should be installed and started during system boot. It includes options like `WantedBy`, `RequiredBy`, `Alias`, and `Also`.
4.  `[Socket]` Defines a socket unit file, which is used to listen for incoming network connections or file system events.
5.  `[Device]` Defines a device unit file, which is used to manage a device file in the file system.
6.  `[Mount]` Defines a mount unit file, which is used to manage file system mounts.
7.  `[Automount]` Defines an automount unit file, which is used to automatically mount file systems on demand.
8.  `[Target]` Defines a target unit file, which is used to group and order other units during system boot.

### Service
The "Service" section contains directives that define how the service should be executed and managed by systemd. Here are some commonly used directives found in the "Service" section:
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