a file manager for GNOME

open local folder: `nautilus . &`
### Troubleshoot
fix the bomb icon for SVN directories in nautilus:
	One thing that might help is restarting the status checker.
	You can do this by killing the checkerservice.py process.
	Run "ps aux | grep rabbitvcs" and kill the process that says checkerservice.py.
	Once you do that, restart nautilus (nautilus -q) and see what happens.