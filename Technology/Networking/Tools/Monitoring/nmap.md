Network exploration tool and security / port scanner

[guide](https://www.freecodecamp.org/news/what-is-nmap-and-how-to-use-it-a-tutorial-for-the-greatest-scanning-tool-of-all-time/)

To scan local network for IP addresses, provide it with the [[Subnet]] to scan:
```sh
sudo nmap -sn 10.100.102.0/24
```
`-sn`: This flag tells Nmap to perform a **SYN scan**. This is a fast and efficient way to identify active devices without sending full port scans. It essentially sends a connection initiation packet (SYN) and checks for a response (SYN-ACK) indicating an active host.