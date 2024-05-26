#linux #network 
dump traffic on a network

 [guide](https://www.tecmint.com/12-tcpdump-commands-a-network-sniffer-tool/)

display available interfaces:   `tcpdump -D`
capture on an *if* called *eth0*:   `sudo tcpdump -i eth0`
capture in *ASCII* format:   `sudo tcpdump -A -i eth0`
capture in *hex*a and *ASCII* format:   `sudo tcpdump -XX -i eth0`
save captured to file:   `sudo tcpdump -w filename.pcap -i eth0`
read captured from file:   `sudo tcpdump -r filename.pcap`
show ip instead of hostname:   `sudo tcpdump -n -i eth0`
capture only tcp:   `sudo tcpdump -i eth0 tcp`
capture from specific port:   `sudo tcpdump -i eth0 port 22`
capture with specific source ip:   `sudo tcpdump -i eth0 src 172.16.0.3`
capture with specific destination ip:   `sudo tcpdump -i eth0 dst 172.16.0.1`
- `-Q [in|out|inout]`  only show incoming/outgoing/both direction packets

sniff packets on eth1
	`sudo tcpdump -nei eth1`