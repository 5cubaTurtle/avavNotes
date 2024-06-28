Show / manipulate the IP routing table. IP routing table determines where network traffic is directed.

`route`: Display routing table 

Options:
- `-v` verbose
- `-n` resolve names to IPs

see outgoing routes:`route -n`. If the output does not contain: 
	Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
	0.0.0.0         192.168.31.254  0.0.0.0         UG    0      0        0 eth1
you can add default getway (router's IP) to establish internet access:
	`route add default gw <X.X.X.X>`

Remove a route: `route del default  gw rpi4remote wlan0`
	since the gateway `rpi4remote` might be resolved through DNS, it might be better to use its IP address directly.

### -host
Specify host route:
```sh
sudo route add -host 10.42.0.10 gw 10.42.0.10 wlan0
```
The `-host` flag is particularly useful when you need to create a routing rule for a specific host rather than a range of IP addresses. It ensures that the specified route is only used for traffic directed at that single IP address, providing precise control over network traffic.

#### Example Without `-host` Flag
If you were to add a route for an entire network, you would typically use:
```sh
sudo route add -net 10.42.0.0/24 gw 10.42.0.1 eth0
```
This command adds a route for the network `10.42.0.0/24`, meaning any traffic destined for any IP address within the `10.42.0.x` range will be routed through `10.42.0.1` via the `eth0` interface.

### Add gateway
Example:
```sh
sudo route add default gw 192.168.1.1 wlan0
sudo sh -c 'echo "nameserver 8.8.8.8" >> /etc/resolv.conf'
```
In this example the *8.8.8.8* server allso added to [[resolve.conf]].

### ChatGPT 4o
Following is an explanation of output of `route`:

The `route` command displays the kernel's IP routing table, which determines where network traffic is directed:
Example output:
```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
default         netbox          0.0.0.0         UG    600    0        0 wlp0s20f3
10.42.0.0       0.0.0.0         255.255.255.0   U     100    0        0 enp0s31f6
10.100.102.0    0.0.0.0         255.255.255.0   U     600    0        0 wlp0s20f3
10.200.200.0    0.0.0.0         255.255.255.0   U     0      0        0 wg0
link-local      0.0.0.0         255.255.0.0     U     1000   0        0 wlp0s20f3
```

Columns:
1. **Destination**: The destination network or host.
2. **Gateway**: The gateway through which the traffic is routed. A `0.0.0.0` entry indicates that no gateway is used (directly reachable network).
3. **Genmask**: The [[netmask]] for the destination network.
4. **Flags**: Various flags indicating the route type.
   - `U`: The route is up.
   - `G`: The route is to a gateway.
   - `H`: The route is to a host.
   - `R`: The route is reinstated after a downed interface comes back up.
   - `D`: The route is dynamically created.
   - `M`: The route is modified.
5. **Metric**: The cost of using this route. Lower values indicate preferred routes.
6. **Ref**: The number of references to this route. Typically 0.
7. **Use**: The number of packets that have been routed via this entry.
8. **Iface**: The network interface used for this route.

### Interpreting Each Entry

1. **Default Route**
   ```
   default         netbox          0.0.0.0         UG    600    0        0 wlp0s20f3
   ```
   - **Destination**: `default` indicates this is the default route used when no other specific route matches.
   - **Gateway**: `netbox` is the gateway for this default route.
   - **Genmask**: `0.0.0.0` means no [[netmask]] is applied.
   - **Flags**: `UG` (Up and Gateway).
   - **Metric**: `600` (the priority of the route; higher value means lower priority).
   - **Iface**: `wlp0s20f3` (the wireless network interface).

2. **Route for 10.42.0.0/24 Network**
   ```
   10.42.0.0       0.0.0.0         255.255.255.0   U     100    0        0 enp0s31f6
   ```
   - **Destination**: `10.42.0.0` network.
   - **Gateway**: `0.0.0.0` indicates no gateway; the network is directly reachable.
   - **Genmask**: `255.255.255.0` ([[netmask]]).
   - **Flags**: `U` (Up).
   - **Metric**: `100`.
   - **Iface**: `enp0s31f6` (the Ethernet network interface).
   
4. 
   - **Iface**: `wg0` (WireGuard virtual network interface).

5. **Link-Local Route**
   ```
   link-local      0.0.0.0         255.255.0.0     U     1000   0        0 wlp0s20f3
   ```
   - **Destination**: `link-local` (addresses in the range 169.254.0.0/16, used for link-local networking).
   - **Gateway**: `0.0.0.0` (directly reachable).
   - **Genmask**: `255.255.0.0`.
   - **Flags**: `U`.
   - **Metric**: `1000`.
   - **Iface**: `wlp0s20f3`.

### Explanation of Two Default Routes:
Having two default routes with different metrics indicates that the system has two potential paths to the internet or outside network. The metric value determines the priority, with the lower metric route being preferred.
### Summary

- The default route directs traffic through the `netbox` gateway on `wlp0s20f3`.
- The `10.42.0.0/24` network is directly reachable via `enp0s31f6`.
- The `10.100.102.0/24` network is directly reachable via `wlp0s20f3`.
- The `10.200.200.0/24` network is directly reachable via `wg0` (WireGuard).
- Link-local addresses are reachable via `wlp0s20f3`.

This routing table directs traffic appropriately based on the destination IP address, using specific interfaces and gateways as defined.