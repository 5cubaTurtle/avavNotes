
setting wireshark to work in non root:
	`sudo dpkg-reconfigure wireshark-common`, chose "Yes" then do:
	`sudo usermod -a -G wireshark $USERNAME`