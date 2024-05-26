
### Paths
kernel log:*/var/logs/syslog.log*
ntework interface: */etc/network/interfaces*

mount a shared folder from windows to ~/Support (use the vers=2.0 option if you get "mount error(112): Host is down")
	sudo mount -t cifs -o vers=2.0,username=support,password=Embedded //192.168.31.50/Desktop ~/Support

	sudo mount.cifs //222.108.151.150/GermanyDMP ./DevShared/ -o user=Windows_7,vers=2.1
### Networking
setup a bridge between port *Eth0* and *Eth1* with address `0.0.0.0`:
	edit the file `/etc/network/interfaces`
		# interfaces(5) file used by ifup(8) and ifdown(8)

		auto lo
		iface lo inet loopback

		iface eth0 inet manual	#set eth0 unacessible from gui

		iface eth1 inet manual

		auto br0
		iface br0 inet static
		bridge_ports eth0 eth1
		address 0.0.0.0
		#netmask 255.255.255.0
		#network 10.0.0.0
		#broadcast 10.0.0.255
		#gateway 10.0.0.138

After entering all the details you need to restart networking services using the following command
    `sudo /etc/init.d/networking restart`
As an user you can see your current hostname with
    `sudo /bin/hostname`
To set the hostname directly you can become root and run
    `sudo /bin/hostname newname`
When your system boots it will automatically read the *hostname* from the file */etc/hostname*