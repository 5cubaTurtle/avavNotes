#network 
command-line tool for controlling NetworkManager
[man](https://developer-old.gnome.org/NetworkManager/unstable/nmcli.html), [ubuntu-guide](https://ubuntu.com/core/docs/networkmanager/configure-wifi-connections) [opensource.com-guide](https://opensource.com/article/20/7/nmcli)

##### get info
general help:  `nmcli help`   or   `nmcli h`
object specific help:  `nmcli <object> h`, for example `nmcli connection help`.
view all saved connections:   `nmcli connection show` or `nmcli c`
- `--active`  this optional flag will only show currently active connections

status of devices (interfaces):   `nmcli -p device`
- `-p`  pretty mode
- `-t`  terse mode

monitor changes on the interfaces: `nmcli monitor`

##### connect to network
connect to wireless network named "bladerangertest_plus":
	`sudo nmcli dev wifi connect bladerangertest_plus password "phoenix2015"`
- `--ask`  will ask for the password if not given
This will automatically create a file in `/etc/NetworkManager/system-connections/`.

##### delete connection
delete saved connection:  `sudo nmcli connection delete <network>`

##### closing connection
closing connection:
`nmcli con down <AP name>`

```shell
nmcli con up id bond0
nmcli con up id port0
nmcli dev disconnect bond0
nmcli dev disconnect ens3
```
example; disconnect connection named bladerangertest:  `nmcli connection down id bladerangertest`

### WiFi
- off wifi:  `nmcli r wifi off`
- scan available wifi networks: `sudo nmcli d wifi rescan`
- list available wifi networks:   `nmcli d wifi`, If ran using [[sudo]] the command will also rescan.
- setup hotspot on wifi iface *wlp0s20f3*:   `nmcli d wifi hotspot ifname wlp0s20f3 ssid myBrnadNewHS password 111333000`. See [[set-up-hotspot]] for a more details.
- close hotspot:   `nmcli c down Hotspot`
- show connection priorities: 
	`nmcli -f NAME,UUID,AUTOCONNECT,AUTOCONNECT-PRIORITY c`
	- `-f, --fields <field,...>|all|common`      specify fields to output
	- No spaces after the `,` between the fields.

### modify
- set connection priority:
	`nmcli connection modify HOME-WIFI connection.autoconnect-priority 10`
	or:`nmcli c mod "mypreferred" conn.autoconnect-p 10`. Lower value indicate higher priority.
 - don't auto-connect:
	`nmcli connection modify HOME-WIFI connection.autoconnect no`
options:
- `connection.autoconnect-retries`. By default, `connection.autoconnect-retries` is set to `-1`, which means Network Manager will retry indefinitely until a connection is successfully established or the network becomes unavailable.

#### Notes:
- established connections are saved to folder */etc/NetworkManager/system-connections*
- The `nmcli connection down` command, deactivates a connection from a device **without preventing** the device from further auto-activation. The `nmcli device disconnect` command, disconnects a device and **prevent** the device from automatically activating further connections without manual intervention.
- scanning all available networks could be achieved with [[iw]] util

#### Configure shared connections
[canonical how-to-guide](https://ubuntu.com/core/docs/networkmanager/configure-shared-connections)
```shell
$ nmcli c add con-name <name> type ethernet ifname <iface> ipv4.method shared ipv6.method ignore $ nmcli c up <name>
```

#### GUI
`nmtui` - Text User Interface for controlling NetworkManager
