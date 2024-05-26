#time

print or set the system date and time

seconds since  epoch (1970):   `date +%s`
set new date and time (changes system and hw clock)
	`timedatectl set-time '2015-11-20 16:14:50'`
However, it might not work if your system has time synchronization enabled (NTP). You need to disable it first with: `sudo timedatectl set-ntp false`. Once disabled, do the previous command again, and it should keep your entry as the current date/time.
To switch back to automatic date, just enable NTP again with: `sudo timedatectl set-ntp true`
Print a string with a date: `date +'Today is %c. A fine day.'`
UTC-formatted time and date value: `date -Iseconds --utc`, used to timestamp [[model-assertion]] file.

set system time:
	`date -s` ...(check man)
set hardware clock:
	`hwclock` ...(check man)
