#python 
`subprocess` module creates and manages processes

[doc](https://docs.python.org/3/library/subprocess.html)
[tutorial](https://pythontect.com/python-subprocess-popen-tutorial/)

### [call()](https://docs.python.org/3/library/subprocess.html#subprocess.call)
Run the command described by _args_. Wait for command to complete, then return the [`returncode`](https://docs.python.org/3/library/subprocess.html#subprocess.Popen.returncode "subprocess.Popen.returncode") attribute.
```python
import subprocess
# Simple comand-line call
subprocess.call("./myscript.sh")

# Comand-line call with arguments
subprocess.call(["./myscript.sh", "arg1", "arg2"])
```
`shell=True` argument tells `call()` to run the command in a shell, allowing you to use shell features like pipes and redirection.

If you need more control over the process, such as running it in the background or reading its output, then [[#[Popen()](https://docs.python.org/3/library/subprocess.html subprocess.Popen)|Popen()]] may be more appropriate. Or, code needing to capture *stdout* or *stderr* should use [`run()`](https://docs.python.org/3/library/subprocess.html#subprocess.run "subprocess.run") instead.

#### execute command as a shell
```python
# Execute the source command within a Bash shell
subprocess.call(["bash", "-c", "source /home/ava/br/env/br.bashrc"])
```

or
```python
subprocess.call(["bash", "-c", "source /home/ava/br/env/br.bashrc; fix_config gazebo localhost; rpi-install"])
```

### [Popen()](https://docs.python.org/3/library/subprocess.html#subprocess.Popen)
`subprocess.popen()` is one of the most useful methods which is used to create a process. This process can be used to run a command or execute binary.

passing some arguments to an external program as a sequence:
```python
Popen(["/usr/bin/git", "commit", "-m", "Fixes a bug."])
```
- Use full path. Resolving the path of _executable_ (or the first item of _args_) is platform dependent.

syntax:
```python
subprocess.Popen(COMMAND,STDIN, STDOUT,STDERR,SHELL)
```
parameters to `Popen`:
-   `COMMAND` is a string or a list which contains the command or binary with its parameters and options.
-   `STDIN` is the standard input which is optional.
-   `STDOUT` is the standard output which is optional.
-   `STDERR` is the standard error which is optional.
-   `SHELL` is used to run specified process in the shell where shell environment is used.
example running a python function in it's own process:
```python
import subprocess

def my_function(arg1, arg2):
    # Function code goes here
    return result

if __name__ == '__main__':
    # Spawn a new process for the function
    process = subprocess.Popen(['python', '-c', 'import sys; sys.path.append(".") ; from your_module import my_function; my_function(arg1, arg2)'])

    # Wait for the process to finish
    process.wait()
```

using as [[contex-manager]]:
```python
with Popen(["ifconfig"], stdout=PIPE, text=True) as proc:
	line = proc.stdout.read()
	print(line)
```
- `stdout=PIPE` without this, no output will be saved to `proc.stdout`
- `text=true` will write [[str]] instead of [[bytes]] by default

### run command over ssh:
[StckOvrflw](https://stackoverflow.com/a/57439663)
```python
import subprocess

# Python 2
subprocess.Popen("ssh {user}@{host} {cmd}".format(user=user, host=host, cmd='ls -l'), shell=True, stdout=subprocess.PIPE, stderr=subprocess.PIPE).communicate()

# Python 3
subprocess.Popen(f"ssh {user}@{host} {cmd}", shell=True, stdout=subprocess.PIPE, stderr=subprocess.PIPE).communicate()
```
