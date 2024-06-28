**Kill processes by name**
`killall` sends a signal to all processes running any of the specified commands.  If no signal name is specified, SIGTERM is sent.
Signals can be specified either by name (e.g.  -HUP or -SIGHUP) or by number (e.g.  -1) or by option -s.

Send [[kill#SIGHUP|SIGHUP]] to the *wap_supplicant* process: `killall -HUP wpa_supplicant`