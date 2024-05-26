#ssh 
[webdoc](https://www.paramiko.org/)
python implementation of [[ssh]] protocol, providing both client and server functionality.

install:  `pip install paramiko`

#### Execute remotely
Copy a script to a remote machine and execute it:
1. Create a client object and connect to the remote machine using SSH:
```python
client = paramiko.SSHClient()
client.set_missing_host_key_policy(paramiko.AutoAddPolicy())
client.connect(hostname=remote_machine_ip_address, username=username, password=password)
```
The line: `client.set_missing_host_key_policy(paramiko.AutoAddPolicy())` sets the [[#missing host key policy]] for the Paramiko SSH client.

2. Create a SFTP client object to transfer the script file to the remote machine:
```python
sftp = client.open_sftp()
sftp.put(local_path_to_script_file, remote_path_to_script_file)
```
[`sftp.put()`](https://docs.paramiko.org/en/stable/api/sftp.html#paramiko.sftp_client.SFTPClient.put)
3. Execute the script file on the remote machine using the SSH client:
```python
stdin, stdout, stderr = client.exec_command('python ' + remote_path_to_script_file)
```
4. Close the SSH and SFTP client connections:
```python
sftp.close()
client.close()
```

#### using SSH key instead of password
```python
# load the SSH key from the specified file
key = paramiko.RSAKey.from_private_key_file('path/to/private/key')
# create the client
client = paramiko.SSHClient()
# set missing host key policy
client.set_missing_host_key_policy(paramiko.AutoAddPolicy())

# Connect to the remote server using the SSH key
client.connect(hostname='remote_machine_ip_address', username='username', pkey=key)
```

#### Missing host key policy
When a client connects to a server over SSH, the server sends its public key to the client to verify its identity. The client then checks this key against its list of known hosts to verify that it is connecting to the correct server.

If the server's public key is not in the client's known hosts list, the client needs to decide what to do. By default, Paramiko will raise an exception if the server's public key is not found in the known hosts list.

However, by setting the missing host key policy to `paramiko.AutoAddPolicy()`, the client will automatically add the server's public key to its known hosts list if it is not already present, and proceed with the connection. This can be useful for cases where you are connecting to a new server for the first time and do not have its public key in the known hosts list.

It's important to note that this can potentially be a security risk, as it opens up the possibility of man-in-the-middle attacks. Therefore, it's important to ensure that you are connecting to the correct server and that the server's public key can be trusted before using this policy.

#### execute local script remotely
Execute a *bash* script remotely:
```python
# define the command to run on the remote machine
command = "bash -s < {}".format('/path/to/local_script.sh')

# execute the command on the remote machine and print the output
stdin, stdout, stderr = ssh.exec_command(command)
print(stdout.read().decode())
```
Execute a *python* script remotely: **???**
```python
import paramiko
import os

# define the SSH connection parameters
ssh = paramiko.SSHClient()
ssh.set_missing_host_key_policy(paramiko.AutoAddPolicy())
ssh.connect('remote_machine_ip', username='username', password='password')

# define the command to run on the remote machine
command = "python -"

# open a channel to execute the command
stdin, stdout, stderr = ssh.exec_command(command)

# read the contents of the local script
local_script = open('/path/to/local_script.py', 'r').read()

# write the contents of the local script to the remote channel
stdin.write(local_script)

# indicate that there is no more input to write to the channel
stdin.channel.shutdown_write()

# read the output from the channel
output = stdout.read().decode()

# print the output from the remote command
print(output)

# close the SSH connection
ssh.close()
```
**???** - not tested

#### troubleshooting
> error: sshexception: server 'plc-107' not found in known_hosts
```python
client = paramiko.sshclient()
client.connect(hostname=dest_host)
```
and i get the following exception: "sshexception: server 'plc-107' not found in known_hosts"

this exception occurs when the remote machine you're trying to connect to is not present in the known_hosts file on your local machine.

alternatively, you can pass the missing_host_key_policy parameter to the sshclient constructor to tell paramiko how to handle missing host keys. for example, you can set it to `paramiko.autoaddpolicy()` to automatically add new host keys to the known_hosts file:
```python
client = paramiko.sshclient()
client.set_missing_host_key_policy(paramiko.autoaddpolicy())
client.connect(hostname=dest_host)
```
note that using autoaddpolicy can be risky in some situations, as it could potentially allow a man-in-the-middle attack if someone were to intercept your connection and present a fake host key. so it's generally better to add host keys to your known_hosts file manually, as described in the first approach.