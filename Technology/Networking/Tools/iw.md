#network 
show / manipulate wireless devices and their configuration

scan wireless networks visible to interface "mlan0":
	`sudo iw dev mlan0 scan | grep SSID`
