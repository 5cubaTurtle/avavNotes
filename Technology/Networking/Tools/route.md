show / manipulate the IP routing table

see outgoing routes:`route -n`. If the output does not contain: 
	Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
	0.0.0.0         192.168.31.254  0.0.0.0         UG    0      0        0 eth1
you can add default getway (router's IP) to establish internet access:
	`route add default gw <X.X.X.X>`