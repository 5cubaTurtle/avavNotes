The ssh-keyscan command is used to gather SSH public keys from a remote host. The command connects to the remote host using the SSH protocol, and retrieves the public keys of the SSH server that is running on that host. The public keys are returned in a format that can be used to verify the identity of the remote host when connecting to it using SSH.

Here is an example of how to use the ssh-keyscan command to retrieve the public keys of a remote host: `ssh-keyscan example.com`

This command will connect to the SSH server running on `example.com`, retrieve its public keys, and print them to the standard output. The output will look something like this:
```sh
# example.com SSH-2.0-OpenSSH_7.4
example.com ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABAQDL4y4D/4+RvRJ1ldFGY/Mf+ZLlIgi....
```
The first line of the output is a comment that identifies the SSH server that was scanned, and the SSH protocol version that it supports. The remaining lines are the public keys of the SSH server, one per line. Each line includes the type of the key (e.g. `ssh-rsa`, `ssh-ed25519`, etc.), followed by the key itself.

The output of `ssh-keyscan` can be used to add the public keys of a remote host to the `known_hosts` file on your local machine, which is used to verify the identity of the remote host when connecting to it using SSH.