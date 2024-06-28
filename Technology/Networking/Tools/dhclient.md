#linux #networking 
Dynamic Host Configuration Protocol Client

examples from [cyberciti](https://www.cyberciti.biz/faq/howto-linux-renew-dhcp-client-ip-address/)

renew IP address on interface:   `sudo dhclient -v -r eth0`
- `-r`  Release  the current lease and stop the running DHCP client as previously recorded in the PID file.
- `-v`   Verbose