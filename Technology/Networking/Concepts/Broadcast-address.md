---
aliases:
  - broadcast address
---
#networking 

The broadcast address is an IP address that allows network data to be sent simultaneously to all hosts on a given [[Subnet|subnetwork]], rather than specifying a particular host. The standard general broadcast address for IP networks is 255.255.255.255, but this broadcast address cannot be used to send a broadcast message to every host on the Internet because routers block it. A more appropriate broadcast address is set to match a specific [[Subnet|subnetwork]]. For example, on the private Class C IP network, 192.168.1.0, the broadcast address is 192.168.1.255. Broadcast messages are typically produced by network protocols such as the Address Resolution Protocol ([[Technology/Networking/Concepts/Protocols/ARP|ARP]]) and the Routing Information Protocol (RIP).