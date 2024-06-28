#linux #networking 
show / manipulate routing, network devices, interfaces and tunnels

[guide](https://linuxize.com/post/linux-ip-command/)

show IPv4 addresses:   `ip -4 a`
show specif interface:   `ip a show <ifname>` (if completes with tab)
add ip on eth0:   `sudo ip address add 192.168.121.45/24 dev eth0`
>[!Note]
>Interface may have several addresses.

remove ip on eth0:   `sudo ip address del 192.168.121.45/24 dev eth0`
alter the state of an *if*:   `ip link set {DEVICE} {up|down}`  (UP or DOWN)
help on ip-address:   `man ip-address`

See if [[Technology/Networking/Concepts/Protocols/ARP|arp]] is used on eth2:(if NOARP appears in <...> then arp is off for eth2)
	`ip link show eth2`
Clear [[Technology/Networking/Concepts/Protocols/ARP|arp]] cache `sudo ip -s -s neigh flush all`
Turn off/on arps on interface eth0
	`sudo ip link set dev eth0 arp off/on`
Routing table `ip route`