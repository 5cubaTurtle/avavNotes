[guide](https://linuxconfig.org/how-to-configure-static-ip-address-on-ubuntu-18-10-cosmic-cuttlefish-linux)
edit the file */etc/netplan/01-network-manager-all.yaml*:
```yaml
# Let NetworkManager manage all devices on this system
network:
  version: 2
  renderer: networkd
  ethernets:
    enp0s31f6:
     dhcp4: no
     addresses: [172.16.0.1/24]
       #     geteway: 192.168.88.1
     nameservers:
      addresses: [8.8.8.8,8.8.4.4]
```
- setting **if** *enp0s31f6* to 172.16.0.1/24. We should change the renderer from NetworkManger.
Then apply changes:   `sudo netplan apply` or `sudo netplan --debug apply` if having errors.