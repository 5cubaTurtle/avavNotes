#copy 

rsync from some ip:home/workbench/bkups/hosts_fixed to locacl dir:
`rsync -vpgt 10.200.200.216:workbench/bkups/hosts_fixed .`
rsync to a host with a different user (*balde-admin* to host *balde*):
`rsync -avP plc2-0.img blade-admin@blade:~/robot-images/`
	options:
	- `-a` archive, archive mode; equals -rlptgoD (no -H,-A,-X). This preserves the directory hierarchy, permissions, and timestamps of the files being transferred.
	 - `-v` verbose
	 - `-h`,` --human-readable` 
	 - `--progress` show progress of transfer.
	 - `-P` same as `--partial --progress` show progress (use for big transferes)
	 - `-g`,` -group`  preserve group
	 - `-r`, `--recursive`
	 -  `-z` compresses the data being transferred, which can help improve performance over slow network connections.
	 - `--exclude <path>` don't copy this subdirectory
	 - `-n` dry run

Copy several files: `rsync <file1> <file2> <file3> <destination>:`

Copy a file(./logFile.h) to a remote machine (username==europe, ip==222.108.151.3, to path: ~/es_gw/)
	`rsync -av --progress -e "ssh -l europ" logFile.h 222.108.151.3:es_gw/`

Sync files from MergerDesk folder to 222.108.151.3's work folder
	`rsync -av --progress -e "ssh -l europ" /home/es/MergeDesk/user_appl/*.[c,h] 222.108.151.3:es_gw/raf_1/user_appl/`
		- `-e` specify the remote shell to use