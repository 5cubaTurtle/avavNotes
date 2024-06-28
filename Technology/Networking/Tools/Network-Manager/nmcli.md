---
doc: https://networkmanager.dev/docs/api/latest/nmcli.html
---
#networking 
command-line tool for controlling [[NetworkManager]]. It can create, display, edit, delete, activate, and deactivate network connections, as well as control and display network device status.

[man](https://developer-old.gnome.org/NetworkManager/unstable/nmcli.html), [ubuntu-guide](https://ubuntu.com/core/docs/networkmanager/configure-wifi-connections) [opensource.com-guide](https://opensource.com/article/20/7/nmcli), `man nmcli-examples`

### info
Show general status: `nmcli`

Prepend `nmcli` to all commands here.
General help:  `help`   or   `h`
Object specific help:  `<object> h`, for example `connection help`.

View all saved connections:   `connection show` or `c`
- `--active`  this optional flag will only show currently active connections
Show connection details: `connection show <Name>`. The *\<Name\>* is from `connection show`.

Status of devices (interfaces):   `-p device`
- `-p`  pretty mode
- `-t`  terse mode
Show device configuration: `device show <iface>`
#### Debugging
Monitor changes on the interfaces: `monitor`
Journal: `journalctl -fu NetworkManager`

### Connection
- established connections are saved to folder */etc/NetworkManager/system-connections*

Connect to wireless network named *myAP*:
	`sudo dev wifi connect myAP password "phoenix2015"`
- `--ask`  will ask for the password if not given

Closing connection: `con down <name>`, to get the `<name>` of the connection run `connection`.
Alternatively: `device disconnect <ifname>` command, disconnects a device and **prevent** the device from automatically activating further connections without manual intervention.

Delete saved connection:  `sudo connection delete <network>`
#### Modify
Syntax: `nmcli connection modify <connection_name> <property> <value>`

Set connection priority:
	`connection modify HOME-WIFI connection.autoconnect-priority 10`
	or:`c mod "mypreferred" conn.autoconnect-p 10`. Higher value is higher priority.
Don't auto-connect:
	`connection modify HOME-WIFI connection.autoconnect no`
Options:
- `connection.autoconnect-retries`. By default, `connection.autoconnect-retries` is set to `-1`, which means Network Manager will retry indefinitely until a connection is successfully established or the network becomes unavailable.

##### Configure connection manually
Following commands modify connection named *Hotspot*:
```sh
nmcli connection modify Hotspot ipv4.method manual
nmcli connection modify Hotspot ipv4.addresses 192.168.1.1/24
nmcli connection modify Hotspot ipv4.gateway 192.168.1.254
nmcli connection modify Hotspot ipv4.dns "8.8.8.8 8.8.4.4"
```
Then restart the connection:
```sh
nmcli connection down Hotspot
nmcli connection up Hotspot
```
See connection details: `c s Hotspot`
#### Configure shared connections
[canonical how-to-guide](https://ubuntu.com/core/docs/networkmanager/configure-shared-connections)
```shell
$ nmcli c add con-name <name> type ethernet ifname <iface> ipv4.method shared ipv6.method ignore
$ nmcli c up <name>
```

### WiFi
- Off wifi:  `r wifi off`
- Show connection priorities: 
	`-f NAME,UUID,AUTOCONNECT,AUTOCONNECT-PRIORITY c`
	- `-f, --fields <field,...>|all|common`      specify fields to output
	- No spaces after the `,` between the fields.
##### Scanning
- Scan available wifi networks: `sudo nmcli d wifi rescan`. Works better with `sudo`.
- List available wifi networks:   `d wifi`, If ran using [[sudo]] the command will also rescan.
- Scanning could also be done using the [[iw]] utility.
#### Hotspot (AP)
- Setup hotspot on wifi iface *wlan0*:   `d wifi hotspot ifname wlan0 ssid myAP password 111333000`. See [[set-up-hotspot]] for a more details.
	- omitting the `password` flag and argument will generate one. Use `d w show-password` to see it.
- Close hotspot:   `c down Hotspot`
- Show password for the AP: `d w show-password`

### UI
`nmtui` - Text User Interface for controlling NetworkManager
