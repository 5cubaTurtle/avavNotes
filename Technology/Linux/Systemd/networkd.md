#### Overview:
`systemd-networkd` is a system service that manages network configurations for `systemd`, the init system widely used in modern Linux distributions. It integrates with other components of the `systemd` ecosystem, such as `systemd-resolved` for DNS resolution and `systemd-timesyncd` for time synchronization.
#### Features:
- **Dynamic Network Configuration**: Automatically configures network interfaces using DHCP, static IPs, or both.
- **Link Aggregation**: Supports bonding and teaming of network interfaces for redundancy and increased throughput.
- **Bridging**: Can create and manage network bridges.
- **VLANs**: Supports Virtual LAN configurations.
- **Integration with `systemd`**: Works seamlessly with other `systemd` services and takes advantage of `systemd`'s capabilities like logging and dependency management.
#### Configuration:
- **Configuration Files**: Network configurations are defined in `.network` and `.netdev` files located in `/etc/systemd/network/` or `/usr/lib/systemd/network/`.
- **Example Configuration**:
```ini
[Match]
Name=enp0s3

[Network]
DHCP=yes
```
##### /etc/systemd/network/
- **Purpose**: This directory contains network configuration files for `systemd-networkd`, a network management service that can configure network interfaces.
- **Contents**: Files in this directory typically have extensions like `.network`, `.netdev`, and `.link`.
    - **`.network` files**: Define network configurations for interfaces.
    - **`.netdev` files**: Define virtual network devices.
    - **`.link` files**: Define low-level hardware settings for network interfaces.
#### Advantages:
- Tight integration with `systemd`.
- Comprehensive feature set covering a wide range of network configurations.
- Good for modern, dynamic network environments with frequent changes.