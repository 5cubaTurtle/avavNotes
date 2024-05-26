Setting up hidden hotspo:
To set up a hidden hotspot using `nmcli`, you can follow these steps:

1. Check if your system supports creating a hotspot. Run the following command:
```sh
nmcli connection show
```
Any wifi device can create a hotspot.

2. Create a new hotspot connection by running the following command:
```sh
nmcli connection add type wifi con-name <connection-name> ifname <interface> ssid <SSID> mode ap hidden yes
```

Replace `<connection-name>` with the desired name for your hotspot connection, `<interface>` with the name of your Wi-Fi interface, and `<SSID>` with the desired SSID for your hidden hotspot.

The `hidden yes` option indicates that the hotspot should be hidden (non-broadcast).

3. Set a password for the hotspot by running the following command:

```sh
nmcli connection modify <connection-name> wifi-sec.key-mgmt wpa-psk wifi-sec.psk <password>
```

Replace `<connection-name>` with the name of your hotspot connection and `<password>` with the desired password for your hotspot.

This command sets the security mode to WPA-PSK and specifies the password.

4. Activate the hotspot by running the following command:

```sh
nmcli connection up <connection-name>
```

Replace `<connection-name>` with the name of your hotspot connection.

This command will start the hidden hotspot and make it available for other devices to connect.

Now, you have set up a hidden hotspot using `nmcli`. Other devices can connect to it by manually entering the SSID and password. Keep in mind that the steps may vary slightly depending on your specific Linux distribution and version.