#linux 
Control the [[systemd]] system and service manager

- start:`sudo systemctl start roscore.service`
- restart:`sudo systemctl restart roscore.service`
- check status:`systemctl status br-always-on.service`
- stop: `systemctl stop br-always-on.service`
- enable: `systemctl enable br-always-on`, this will register the service to start on sign-in. This will create a symbolic link from the system’s copy of the service file (usually in */lib/systemd/system* or */etc/systemd/system*) into the location on disk where systemd looks for autostart files (usually */etc/systemd/system/some_target.target.wants*. `enable` will not start the service.
- disable: `systemctl disable br-always-on.service`. This will prevent the service from starting at system boot. Also stop the service as well.
- reload system manager configuration: `systemctl daemon-reload`. This is necessary whenever you make changes to a [[systemd]] service file or any other unit file (such as a timer, socket, or mount file) in order for [[systemd]] to be aware of the changes you made.

List all active units on system: `systemctl list-units`, adding the `--all` flag, will list also the inactive units. Use the flage `--type=service` to show only services.

#### Displaying a Unit File
see the unit file of the *atd* scheduling daemon: `systemctl cat atd.service`

#### Displaying Dependencies
`systemctl list-dependencies sshd.service`
This will display a hierarchy mapping the dependencies that must be dealt with in order to start the unit in question. Dependencies, in this context, include those units that are either required by or wanted by the units above it.

#### [Masking units](https://www.digitalocean.com/community/tutorials/how-to-use-systemctl-to-manage-systemd-services-and-units#masking-and-unmasking-units)
`sudo systemctl mask nginx.service`
This will prevent the Nginx service from being started, automatically or manually, for as long as it is masked. To unmask:
`sudo systemctl unmask nginx.service`

#### [Editing](https://www.digitalocean.com/community/tutorials/how-to-use-systemctl-to-manage-systemd-services-and-units#editing-unit-files) Unit Files
`sudo systemctl edit nginx.service`
This will be a blank file that can be used to override or add directives to the unit definition. A directory will be created within the */etc/systemd/system* directory which contains the name of the unit with `.d` appended. For instance, for the nginx.service, a directory called *nginx.service.d* will be created.

Within this directory, a snippet will be created called *override.conf*. When the unit is loaded, systemd will, in memory, merge the override snippet with the full unit file. The snippet’s directives will take precedence over those found in the original unit file.