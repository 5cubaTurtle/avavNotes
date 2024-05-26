#linux 
nc — arbitrary TCP and UDP connections and listens
The nc (or netcat) utility is used for just about anything under the sun involving TCP, UDP, or UNIX-domain sockets.  It can open TCP connections, send UDP packets, listen on arbitrary TCP and UDP ports, do port scanning, and deal with both IPv4 and IPv6.  Unlike telnet(1), nc scripts nicely, and separates error messages onto standard error instead of sending them to standard output, as telnet(1) does with some.

check ssh connection on port *443*: `nc -vz bitbucket.org 443`. see [[#Port Scanning]].

### Sending a text
sending a text message between 2 netcats:
1. Check your own ip:   `hostname -I`
	output:   `AAA.BBB.CCC.DDD`
2. listen on  port XXXX:   `nc -l XXXX`
3. on the sending machine:   `nc AAA.BBB.CCC.DDD XXXX`
4. type text and send by entering

### Port Scanning
It may be useful to know which ports are open and running services on a target machine.  The -z flag can be used to tell nc to report open ports, rather than initiate a connection.
Usually it's useful to turn on verbose output to stderr by use this option in conjunction with -v option.

For example:

	   $ nc -zv host.example.com 20-30
	   Connection to host.example.com 22 port [tcp/ssh] succeeded!
	   Connection to host.example.com 25 port [tcp/smtp] succeeded!

The port range was specified to limit the search to ports 20 - 30, and is scanned by increasing order (unless the -r flag is set).

You can also specify a list of ports to scan, for example:

	   $ nc -zv host.example.com http 20 22-23
	   nc: connect to host.example.com 80 (tcp) failed: Connection refused
	   nc: connect to host.example.com 20 (tcp) failed: Connection refused
	   Connection to host.example.com port [tcp/ssh] succeeded!
	   nc: connect to host.example.com 23 (tcp) failed: Connection refused

The ports are scanned by the order you given (unless the -r flag is set).

Alternatively, it might be useful to know which server software is running, and which versions.  This information is often contained within the greeting banners.  In order to retrieve these, it is necessary to first make a connection, and then break the connection when the banner has been retrieved.  This can be accomplished by specifying a small timeout with the -w flag, or perhaps by issuing a "QUIT" command to the server:

	   $ echo "QUIT" | nc host.example.com 20-30
	   SSH-1.99-OpenSSH_3.6.1p2
	   Protocol mismatch.
	   220 host.example.com IMS SMTP Receiver Version 0.84 Ready
