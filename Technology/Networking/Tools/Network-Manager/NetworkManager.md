---
wiki: https://en.wikipedia.org/wiki/NetworkManager
doc: https://www.networkmanager.dev/docs/
---
### [Configuration files](https://networkmanager.dev/docs/admins/#configuration-files)
Located at */etc/NetworkManager/*
### [Unmanaging devices](https://networkmanager.dev/docs/admins/#unmanaging-devices)
If you want the choice to persist after a reboot, add the following snippet to configuration:
```ini
[device-enp1s0-unmanage]
match-device=interface-name:enp1s0
managed=0
```
Then, remember to reload configuration with `systemctl reload NetworkManager`.

### Debugging
See debugging section in [man](https://networkmanager.dev/docs/api/latest/NetworkManager.html)

### Connection
[man](https://networkmanager.dev/docs/api/latest/nm-settings-nmcli.html)

### Dispatcher
[man](https://networkmanager.dev/docs/api/latest/NetworkManager-dispatcher.html)

### Description
The Network Manager is a network management service in Linux that provides a high-level interface for configuring and managing network connections. It is designed to simplify the management of network settings and provide a consistent experience across different Linux distributions.

Here's a simplified overview of how the Network Manager works:
1. Network Manager daemon: The Network Manager daemon (`NetworkManager`) runs as a background service on the Linux system. It is responsible for coordinating network-related tasks.
2. User interface and applets: Network Manager provides user interfaces such as command-line tools ([[nmcli]]), graphical frontends (`nm-applet` or `nmtui`), and system tray applets. These interfaces allow users to interact with Network Manager and configure network connections.
3. Connection profiles: Network Manager uses connection profiles to store and manage network settings. A connection profile represents a specific network configuration, including information like network name (SSID), security settings, IP address assignment ([[DHCP]] or static), DNS configuration, etc. Connection profiles can be created manually or automatically detected when connecting to a network.
4. Connection states: Network Manager manages the state of network connections. It tracks the availability of network devices (such as Ethernet, Wi-Fi, or mobile broadband) and maintains the state of each connection profile (connected, disconnected, activating, etc.).
5. Connection control: When a network connection is established or modified, Network Manager communicates with the relevant networking subsystems to configure the network interface and apply the specified settings. This includes handling authentication, encryption, IP address assignment, and routing.
6. Automatic connection management: Network Manager can automatically detect and connect to known networks based on predefined connection rules. For example, it can prioritize Wi-Fi networks, auto-connect to a preferred network when available, or switch between different network interfaces based on availability.
7. Event-based handling: Network Manager monitors network events, such as changes in network connectivity or network device availability. It dynamically reacts to these events and performs the necessary actions, such as connecting to a new network, reconfiguring existing connections, or updating network status in the user interface.

Overall, the Network Manager provides a centralized and consistent approach to managing network connections in Linux, offering a user-friendly interface and automated handling of various networking tasks. It simplifies network configuration and improves the user experience by abstracting the underlying complexities of network management.

`systemd-networkd` and `dhcpcd` are two different networking services for managing network configurations on Linux systems. They are used to configure and manage network interfaces, assign IP addresses, handle DHCP (Dynamic Host Configuration Protocol), and manage other network-related tasks. Here's an overview of each:
### Links
[arch-doc](https://wiki.archlinux.org/title/NetworkManager)

