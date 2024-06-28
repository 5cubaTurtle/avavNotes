enter a system sleep state until specified wakeup time

```sh
rtcwake -m mem -s $slpres         #suspending the machine for a short time
```
- `-m`,` --mode mode` Go into the given standby state.  Valid values for mode are:
	- `standby` ACPI  state S1.  This state offers minimal, though real, power savings, while providing a very low-latency transition back to a working system.  This is the default mode.
	- `freeze` The processes are frozen, all the devices are suspended and all the processors idled.  This state is a general state that does not need any  platform-specific  sup‐port, but it saves less power than Suspend-to-RAM, because the system is still in a running state (Available since Linux 3.9.)
	- `mem` ACPI  state S3 (Suspend-to-RAM).  This state offers significant power savings as everything in the system is put into a low-power state, except for memory, which is placed in self-refresh mode to retain its contents.
	- `disk` ACPI state S4 (Suspend-to-disk).  This state offers the greatest power savings, and can be used even in the absence of low-level platform support for power  management.  This state operates similarly to Suspend-to-RAM, but includes a final step of writing memory contents to disk.
	- `off` ACPI state S5 (Poweroff).  This is done by calling '/sbin/shutdown'.  Not officially supported by ACPI, but it usually works.
	- `no` Don't suspend, only set the RTC wakeup time.
	- `on` Don't suspend, but read the RTC device until an alarm time appears.  This mode is useful for debugging.
	- `disable` Disable a previously set alarm.
	- `show` Print alarm information in format: "alarm: off|on  \<time\>".  The time is in ctime() output format, e.g. "alarm: on  Tue Nov 16 04:48:45 2010".