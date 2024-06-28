The `/var` directory in Linux and other Unix-like operating systems stands for "variable." It is used to store files that are expected to change frequently:
1. **Log Files**: 
   - `/var/log`: Contains system logs and application logs. For example, `syslog` and `auth.log`.
2. **Spool Directories**:
   - `/var/spool`: Holds spooled data waiting for processing, such as print jobs (`/var/spool/cups`) and mail queues (`/var/spool/mail`).
3. **Cache Data**:
   - `/var/cache`: Stores cached data for applications, reducing the need to recompute or refetch data.
4. **Temporary Files**:
   - `/var/tmp`: Contains temporary files that need to persist between system reboots, unlike `/tmp` which is typically cleared on reboot.
5. **Lock Files**:
   - `/var/lock`*: Holds lock files used by programs to indicate that a resource is being used.
6. **Web and FTP Data**:
   - `/var/www`: Default location for web server files.
   - `/var/ftp`: Default location for FTP server files.
7. **Database Files**:
   - `/var/lib`: Contains variable state information used by programs, such as databases and application state files. For example, `/var/lib/mysql` for MySQL databases.
8. **Runtime Data:**
	- `/var/run`: traditionally used to store runtime data, has been replaced by `/run` in many modern Linux distributions. However, some systems still maintain a [[ln|symlink]] from `/var/run` to `/run` for compatibility.