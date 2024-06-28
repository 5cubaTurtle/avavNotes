#linux, #networking 
DNS lookup utility

to querry the router for DHCP clients:  `dig <@router-ip> <client>`
example:  `dig @192.168.88.1 rubin`, this will return the ip of the hostname rubin as it saved in the router's DHCP server leases table.
