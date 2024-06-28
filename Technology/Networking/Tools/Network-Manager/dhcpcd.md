`dhcpcd` (DHCP Client Daemon) is a standalone [[DHCP]] client used to configure network interfaces on Linux and other Unix-like systems. It primarily handles obtaining IP addresses and other network configuration parameters from a DHCP server.

#### Features:
- **DHCP Client**: Obtains and manages IP addresses and network settings via [[DHCP]].
- **IPv4 and IPv6 Support**: Handles both IPv4 and IPv6 configurations.
- **Static Configuration**: Can also handle static IP configurations.
- **Hooks and Scripting**: Supports running custom scripts on certain events like obtaining a lease or losing connectivity.

#### Configuration:
- **Configuration Files**: Configurations are typically found in `/etc/dhcpcd.conf`.
- **Example Configuration**:
```ini
interface enp0s3
static ip_address=192.168.1.10/24
static routers=192.168.1.1
static domain_name_servers=192.168.1.1`
```

#### Advantages:
- Lightweight and simple to set up, making it suitable for minimalistic or embedded systems.
- Independence from [[systemd]], which can be beneficial for systems not using `systemd`.
- Versatile with extensive options for custom scripting and hooks.