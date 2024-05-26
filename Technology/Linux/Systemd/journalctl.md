#linux 
Query the [[systemd]] journal

tail the [[systemd]] logs related to br-master process:   `journalctl -f -u br-master`
- `-f, --follow`   Show only the most recent journal entries, and continuously print new entries as they are appended to the journal.
- `-u, --unit=UNIT|PATTERN`  Show messages for the specified systemd unit UNIT (such as a service unit), or for any of the units matched by PATTERN.

see disk usage:`journalctl --disk-usage`
reduce disk usage to 200MB:`journalctl --vacuum-size=200M`
delete archives older than a day: `journalctl --vacuum-time=1days`
reduce the number of archived files to 2:`journalctl --vacuum-files=2`
