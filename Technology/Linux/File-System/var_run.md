The `/var/run` directory, traditionally used to store runtime data, has been replaced by `/run` in many modern Linux distributions. However, some systems still maintain a symlink from `/var/run` to `/run` for compatibility.
### Purpose of `/run`
1. **Runtime Data**: Stores transient system information that is required during the system’s operation and typically cleared on reboot.
2. **PID Files**:
   - Contains PID (Process ID) files, which keep track of the running processes. For example, `/run/nginx.pid` stores the PID of the Nginx web server.
3. **Sockets**:
   - Stores UNIX socket files used for inter-process communication (IPC). For example, `/run/docker.sock` for Docker.
4. **Lock Files**:
   - Contains lock files to manage resource access. For example, `/run/lock/subsys` stores lock files for system services.
5. **System State Files**:
   - Stores various system state files needed for managing services and daemons. For example, `/run/systemd` contains data used by the systemd init system.
### Key Points
- **Volatile**: The contents of `/run` (or `/var/run`) are volatile and are not preserved between reboots.
- **Early Boot**: `/run` is usually mounted early in the boot process, often as a tmpfs (temporary filesystem), to ensure it is writable even before the main filesystem is fully initialized.
### Typical Layout
- **/run/user**: Contains runtime data for user sessions, typically separated by user ID (e.g., `/run/user/1000`).
- **/run/lock**: Used for lock files, preventing multiple processes from accessing the same resource concurrently.
- **/run/shm**: Symlink to `/dev/shm`, used for shared memory segments.
