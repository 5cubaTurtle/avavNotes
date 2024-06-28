Wi-Fi Protected Access client and IEEE 802.1X supplicant.

`wpa_supplicant -iwlan0 -Dnl80211 -c/etc/wpa_supplicant.conf`

### Options
Most command line options have global scope. Some are given per interface, and are only valid if at least one `-i` option is specified, otherwise they're ignored. Option groups for different interfaces must be separated by `-N` option.
Flags:
- `-d` Increase debug level. `-dd` Increase it further.
- `-B` run in the background

### systemd service
The [[systemd]] wpa_supplicnat [[Daemon|daemon]] will restart if it is stopped using [[systemctl]]. To fully stop ressurection of the service remove the file */usr/share/dbus-1/system-services/fi.w1.wpa_supplicant1.service*. 
