To stop any running background commands started by a Bash script when the script fails, you can use the trap command to set up a signal handler that catches the ERR signal (which is triggered when a command in the script fails) and runs a cleanup function that stops any running background commands.

Here's an example script that demonstrates how to use trap to stop background commands when the script fails:
```sh
#!/bin/bash

function cleanup {
  echo "Cleaning up..."
  kill $(jobs -p)
}

trap cleanup ERR

# Start some background commands
command1 &
command2 &

# Wait for the commands to complete
wait

# Exit successfully
exit 0
```
This script defines a cleanup function that simply kills any running background jobs using jobs -p, which lists the process IDs (PIDs) of all running jobs, and kill, which sends a SIGTERM signal to each job's PID to request that it stop running.

The trap command is used to set up a signal handler that runs the cleanup function when the ERR signal is caught. This signal is triggered when a command in the script fails, so the cleanup function is guaranteed to run whenever the script fails.

The script then starts some background commands (in this case, command1 and command2), waits for them to complete using wait, and exits successfully.

If any of the background commands fail while the script is running, the cleanup function will be run to stop them before the script exits. This ensures that no background commands are left running after the script fails.
