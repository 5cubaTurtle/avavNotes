---
wiki: https://en.wikipedia.org/wiki/Dynamic_Host_Configuration_Protocol
aliases:
  - Dynamic Host Configuration Protocol
---
#networking 
The **Dynamic Host Configuration Protocol** (**DHCP**) is a [network management protocol](https://en.wikipedia.org/wiki/Network_protocol "Network protocol") used on [Internet Protocol](https://en.wikipedia.org/wiki/Internet_Protocol "Internet Protocol") (IP) networks for automatically assigning [IP addresses](https://en.wikipedia.org/wiki/IP_address "IP address") and other communication parameters to devices connected to the network using a [client–server](https://en.wikipedia.org/wiki/Client%E2%80%93server "Client–server") architecture.

- **IP Address Assignment**: DHCP servers lease IP addresses to devices for a specific period.
- **Configuration Parameters**: Can provide [[Netmask|subnet masks]], default gateways, and DNS server addresses.


## General Relationship between DHCP and DNS

#### DHCP (Dynamic Host Configuration Protocol)

- **Purpose**: DHCP automates the process of assigning IP addresses and other network configuration parameters to devices on a network.
- **Functionality**:
  - **IP Address Assignment**: DHCP servers lease IP addresses to devices for a specific period.
  - **Configuration Parameters**: Along with IP addresses, DHCP can provide subnet masks, default gateways, and DNS server addresses.

#### DNS (Domain Name System)

- **Purpose**: DNS translates human-readable domain names (e.g., www.example.com) into IP addresses (e.g., 192.168.1.1) that computers use to identify each other on the network.
- **Functionality**:
  - **Name Resolution**: DNS servers resolve domain names to IP addresses.
  - **Directory Services**: DNS acts as a directory service for the Internet, enabling users to access websites using domain names instead of IP addresses.

#### Interaction Between DHCP and DNS

- **Dynamic DNS Updates**: When a DHCP server assigns an IP address to a device, it can also update the DNS records to map the hostname of the device to the newly assigned IP address.
- **DNS Server Assignment**: DHCP can provide devices with the IP addresses of DNS servers, enabling devices to perform name resolution.

### DHCP and DNS in NetworkManager on Linux

#### NetworkManager

- **Purpose**: NetworkManager is a utility for simplifying the configuration and management of network interfaces, especially in dynamic networking environments such as laptops and mobile devices.
- **Functionality**:
  - **Interface Management**: It manages both wired and wireless network interfaces.
  - **Connection Profiles**: It uses connection profiles to store network settings.

#### DHCP in NetworkManager

- **DHCP Client**: NetworkManager can use the DHCP protocol to obtain IP addresses and network configuration parameters for network interfaces.
- **Configuration**:
  - **Automatic Configuration**: When a connection profile is set to use DHCP (`ipv4.method auto`), NetworkManager will automatically request an IP address and other settings from a DHCP server.
  - **Custom DHCP Options**: Users can customize DHCP options, such as client identifiers or specific DHCP servers.

#### DNS in NetworkManager

- **DNS Server Assignment**: When a DHCP lease is obtained, NetworkManager can receive DNS server addresses from the DHCP server and configure the system to use these servers for DNS resolution.
- **DNS Configuration**:
  - **Automatic**: NetworkManager can automatically configure the system's DNS settings based on the information received from DHCP.
  - **Manual**: Users can manually specify DNS servers in connection profiles (`ipv4.dns`).
- **DNS Plugin**: NetworkManager can use different DNS plugins (e.g., `dnsmasq` or `systemd-resolved`) to handle DNS resolution.

### Example: Configuring DHCP and DNS with NetworkManager

#### DHCP Configuration

1. **Automatic IP Configuration**:
   ```sh
   nmcli connection modify <connection-name> ipv4.method auto
   ```
   This sets the connection to use DHCP for IP address assignment.

2. **Custom DHCP Options**:
   ```sh
   nmcli connection modify <connection-name> ipv4.dhcp-client-id "my-client-id"
   ```

#### DNS Configuration

1. **Automatic DNS Configuration**:
   By default, DNS servers provided by the DHCP server are used.
   
2. **Manual DNS Configuration**:
   ```sh
   nmcli connection modify <connection-name> ipv4.dns "8.8.8.8 8.8.4.4"
   ```

### Example Scenario

Suppose you have a connection profile named `my-wifi` on a Linux machine using NetworkManager. You want to use DHCP to obtain an IP address but specify Google DNS servers manually.

1. **Set the connection to use DHCP**:
   ```sh
   nmcli connection modify my-wifi ipv4.method auto
   ```

2. **Specify Google DNS servers manually**:
   ```sh
   nmcli connection modify my-wifi ipv4.dns "8.8.8.8 8.8.4.4"
   ```

3. **Activate the connection**:
   ```sh
   nmcli connection up my-wifi
   ```

This configuration will make NetworkManager use DHCP to obtain the IP address and other settings, but override the DNS servers with the manually specified ones.

### Summary

- **DHCP** assigns IP addresses and other network settings, potentially including DNS server addresses.
- **DNS** resolves domain names to IP addresses.
- In **NetworkManager**, DHCP can automatically configure both IP addresses and DNS servers, while users can manually specify DNS servers if needed.