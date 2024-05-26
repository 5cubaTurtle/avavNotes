#process 
A snapshot of the current processes
help: `ps --help`

In Debian Linux, the `ps` command is used to display information about running processes. The `ps -ef` command is a commonly used variant of the `ps` command that displays information about all running processes in the system.

Here's what the different columns of the output of `ps -ef` command represent:
-   `UID`: the user ID of the user who owns the process
-   `PID`: the process ID of the process
-   `PPID`: the process ID of the parent process that started this process
-   `C`: the CPU utilization of the process
-   `STIME`: the start time of the process
-   `TTY`: the terminal associated with the process (or `?` if none)
-   `TIME`: the amount of CPU time used by the process
-   `CMD`: the command used to start the process

For example, a typical output of the `ps -ef` command might look like this:
```sh
UID        PID  PPID  C STIME TTY          TIME CMD
root         1     0  0 Nov29 ?        00:00:01 /sbin/init
root         2     0  0 Nov29 ?        00:00:00 [kthreadd]
root         3     2  0 Nov29 ?        00:00:00 [rcu_gp]
```
In this example, we can see that there are three processes currently running, with process IDs of `1`, `2`, and `3`. The first process is owned by the root user, has a parent process ID of `0` (indicating that it was started by the system), and is running the `/sbin/init` command. The second and third processes are kernel threads, which do not have a command associated with them.
You can use the [[Technology/Linux/utils/Search/grep|grep]] command to filter the output and find specific processes.

user oriented format: `ps u`
