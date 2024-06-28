---
aliases:
  - subnetwork
  - subnetting
tags:
  - networking
---
[wiki](https://en.wikipedia.org/wiki/Subnet)
Computers that belong to the same subnet are addressed with an identical group of its [most-significant bits](https://en.wikipedia.org/wiki/Most-significant_bit) of their [IP addresses](https://en.wikipedia.org/wiki/IP_address "IP address"). This results in the logical division of an IP address into two fields: the _network number_ or _routing prefix_, and the _rest field_ or _host identifier_. The _rest field_ is an identifier for a specific [host](https://en.wikipedia.org/wiki/Host_(network) "Host (network)") or network interface.

The _routing prefix_ may be expressed as the first address of a network, written in [Classless Inter-Domain Routing](https://en.wikipedia.org/wiki/Classless_Inter-Domain_Routing "Classless Inter-Domain Routing") (CIDR) notation, followed by a slash character (_/_), and ending with the bit-length of the prefix. For example, _198.51.100.0/24_ is the prefix of the [Internet Protocol version 4](https://en.wikipedia.org/wiki/Internet_Protocol_version_4 "Internet Protocol version 4") network starting at the given address, having 24 bits allocated for the network prefix, and the remaining 8 bits reserved for host addressing. Addresses in the range _198.51.100.0_ to _198.51.100.255_ belong to this network, with _198.51.100.255_ as the subnet [[Broadcast-address|broadcast address]].

For IPv4, a network may also be characterized by its [[Netmask|subnet mask]].
