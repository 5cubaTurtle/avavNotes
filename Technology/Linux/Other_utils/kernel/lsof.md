#linux 
list open files

See which files are deleted but still take up space:  `sudo lsof|grep deleted`
- the process which is using these files, is not relenquishing (closing) them

Check which process/service is buonded to port 5459 or ip 10.0.0.17:
	`sudo lsof -i :5459`
	`sudo lsof -i @10.0.0.17`