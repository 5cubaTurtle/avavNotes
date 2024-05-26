#network #vpn 
set and retrieve configuration of WireGuard interfaces

[wireguard.com - quickstart](https://www.wireguard.com/quickstart/)

to work with wireguard, in */etc/wireguard/* folder, you need the files *wg0.conf* and *public.key*.
start wg interface:``wg-quick up wg0
stop wg interface:`wg-quick down wg0`

add client key to server at file:  `/etc/wireguard/wg0.conf`.
For the edit to teke affect, reload the configuration file:
```shell
wg setconf wg0 <(wg-quick strip /etc/wireguard/wg0.conf)
```

to stop Wireguard functionality rename/delete the file */etc/wireguard/wg0.conf* 

check status of the wg agent on the system:`systemctl status wg-quick@wg0.service`
