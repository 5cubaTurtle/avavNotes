#linux 
Query the [[systemd]] journal

Tail the [[systemd]] logs related to br-master process:   `journalctl -f -u br-master`
- `-f, --follow`   Show only the most recent journal entries, and continuously print new entries as they are appended to the journal.
- `-u, --unit=UNIT|PATTERN`  Show messages for the specified systemd unit UNIT (such as a service unit), or for any of the units matched by PATTERN.
- `-S, --since=, -U, --until=` Limit log by a point in time, e.g., `journalctl -S yesterday`, will show only entries since yesterday.

Printing to [[journalctl|journal]] we need flush the buffer after calling the [[print()]] statements. To do that use the [[sys]] package: 
### Disk usage
See disk usage:`journalctl --disk-usage`
Reduce disk usage to 200MB:`journalctl --vacuum-size=200M`
Delete archives older than a day: `journalctl --vacuum-time=1days`
Reduce the number of archived files to 2:`journalctl --vacuum-files=2`
