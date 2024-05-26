the “d” at the end of `systemd` stands for daemon. To tick all the boxes, a service must be:
- Integrated with `systemd` through a service unit file
- Launched at startup
- Controllable using `systemctl`, the [control interface](https://www.man7.org/linux/man-pages/man1/systemctl.1.html) for `systemd`
- Able to write to the journal

A service [[unit-file]] typically has a file extension of `.service` and is located in the `/etc/systemd/system` directory or `/usr/lib/systemd/system` directory. It contains directives that specify how the service should be started, stopped, and managed by systemd.

#### set up systemd service
To ensure that a script starts automatically on boot, set up a systemd service:
- Create service description file (*unit file*) at */etc/systemd/system/\<service-name\>.service*.
*pigpiod.service* example for such file:
```sh
[Unit]
Description=Pigpio daemon

[Service]
Type=forking
ExecStart=/usr/bin/pigpiod
Restart=always
User=root

[Install]
WantedBy=multi-user.target
```
This defines a systemd service for [[pigpiod]] that runs as a daemon, restarts automatically if it crashes, and is started as the root user.
5.  Save the file and exit the text editor.
6.  Reload systemd to make it aware of the new service by running the command `sudo systemctl daemon-reload`.
7.  Enable the service to start on boot by running the command `sudo systemctl enable pigpiod.service`.
8.  Finally, start the service by running the command `sudo systemctl start pigpiod.service`. This will start pigpiod and also ensure that it starts automatically on subsequent boots.

#### determine the script file of a service
I want to find out the script file of the service *br-always-on.service*. So I check it's status:
```shell
ubuntu@PLC-103:~$ sudo systemctl status br-always-on.service 
● br-always-on.service - Blade Ranger ROS always on listener
     Loaded: loaded (/lib/systemd/system/br-always-on.service; enabled; vendor preset: enabled)
     Active: active (running) since Tue 2023-01-10 19:34:06 IST; 14h ago
   Main PID: 574 (python3)
      Tasks: 18 (limit: 4371)
     CGroup: /system.slice/br-always-on.service
             └─574 python3 /usr/bin/br-always-on
```
From the *Loaded* section we note the path of the *unit-file*: */lib/systemd/system/br-always-on.service*
Alternatively run `systemctl cat br-always-on`.

The location of the executable file is stored in *ExecStart* variable:
```shell
ubuntu@PLC-103:~$ cat /lib/systemd/system/br-always-on.service
[Unit]
Description=Blade Ranger ROS always on listener
After=roscore.service
Requires=roscore.service

[Service]
ExecStart=/usr/bin/br-always-on
RestartSec=10
Restart=always

[Install]
WantedBy=default.target
```
