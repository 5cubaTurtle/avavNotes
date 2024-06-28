#ssh
OpenSSH authentication key utility
ssh-keygen generates, manages and converts authentication keys for [[ssh]].

[ubuntu ssh-key guide](https://help.ubuntu.com/community/SSH/OpenSSH/Keys)

Generate key using default settings:`ssh-keygen`
Options (the following options work on *~/.ssh/know_hosts* by default):
	- `-F <hostname>`  -  check keys for a specific [[hostname]]
	- `-R <hostname>` -  delete all keys for the hostname
	- `-f <filename>` -  work on file other than *~/.ssh/know_hosts*
Change the comment of the file *bitbucket_raycatch*: `ssh-keygen -cf bitbucket_raycatch`
Print the contents of the key *bitbucket_raycatch*: `ssh-keygen -yf bitbucket_raycatch`

#### key generation
syntax:
```sh
ssh-keygen -t <type> -b <bits> -C <comment> -f <file>
```

generate keys   `ssh-keygen -t rsa -b 4096`
- `-t <type>`  sets the key type "rsa"(default) or "dss"
- `-b <bits>`  encryption level (default 3072 bits)
-   `-C <comment>`: Adds a comment to the key. This is typically used to identify the key, such as the hostname or email address of the user.
-   `-f <file>`: Specifies the name of the file to which the key should be saved. This allows you to specify the name and location of the key.

save *passphrase* (if you used one) into your password manager

generate an additional RSA key with 2048 bits and save it to a file called "my_new_key":
```sh
ssh-keygen -t rsa -b 2048 -C "my_new_key" -f my_new_key
```

#### Passphrase
You will be prompted to enter a *passphrase* to protect the key. You can enter a *passphrase* to add an extra layer of security to the key, or leave it blank if you don't want to use a *passphrase*. You will need this *passphrase* the first time you attempt to use the key for logging in (such as git push, git pull, and git fetch). Providing a password will prevent other users with access to the device from using your keys.

#### Key file
After the key is generated, you will see a message indicating where the key was saved. The public key will be saved in the file specified with the `-f` option, and the private key will be saved in the same location with the `.pub` extension. If you specify the same file name for multiple keys, the previous key will be overwritten.

#### Registering the key on remote
You can then copy the public key to the remote server using the [[ssh-copy-id]] command, this will add the key to the authorized_keys file on the remote server:
`ssh-copy-id user@remote_host`
> You will be prompted for the *passphrase* the first time you attempt to log in.

## [Coupling local git server to bitbucket using ssh keys](https://support.atlassian.com/bitbucket-cloud/docs/set-up-personal-ssh-keys-on-linux/)
### Install OpenSSH on Linux
To install OpenSSH, we recommend using the OpenSSH package provided by your Linux distribution.
- For Debian, Ubuntu, Linux Mint, and other Debian-based distributions:
	`sudo apt update && sudo apt install openssh-client`
- For Fedora, CentOS, Red Hat Enterprise Linux, Oracle Linux, and other Fedora-based distributions: `sudo dnf install openssh-clients`
- For Arch Linux and other Arch Linux-based distributions: `sudo pacman -Sy openssh`
- For SUSE Linux, openSUSE Linux, and other SUSE-based distributions: `sudo zypper install openssh`
In the terminal, check that OpenSSH has been successfully installed by running the following command: `ssh -V`. The output should show the installed version of OpenSSH.

### Start the SSH agent
To allow git to use your SSH key, an SSH agent needs to be running on your device.

To check if it is already running, run the ps command. If the ssh-agent is already running, it should appear in the output, such as:

`$ ps -auxc | grep ssh-agent
```sh
myusername 3291 0.0 0.0 6028 464 ? Ss 07:29 0:00 ssh-agent
```
To start the agent, run: `eval $(ssh-agent)`

You may need to add this command to your *~/.bashrc,* *~/.zshrc*, *~/.profile*, or equivalent shell configuration file. Adding this command to a shell configuration file will ensure the agent is running when you open a terminal.

### Create an SSH key pair
To create an SSH key pair:
1. Navigate to your home: `cd ~`
2. Generate a SSH key pair using ssh-keygen, such as:
 `ssh-keygen -t ed25519 -b 4096 -C "{username@emaildomain.com}" -f {ssh-key-name}`
    Where:
    - `{username@emaildomain.com}` is the email address associated with the Bitbucket Cloud account, such as your work email account.
    - `{ssh-key-name}` is the output filename for the keys. We recommend using a identifiable name such as *bitbucket_work*.
        
3. When prompted to Enter passphrase, **you can either provide a password** or leave the password empty. If you input a password, **you will be prompted for this password** each time SSH is used, such as using Git command that contact Bitbucket Cloud (such as git [[push]], git [[pull]], and git [[fetch]]). Providing a password will prevent other users with access to the device from using your keys.

Once complete, ssh-keygen will output two files:
- `{ssh-key-name}` — the _private_ key.
- `{ssh-key-name}.pub` — the _public_ key.

### Add your key to the SSH agent
To add the SSH key to your SSH agent (ssh-agent):
1. Run the following command, replacing the {ssh-key-name} with the name of the _private_ key: `ssh-add {path-to-ssh-key-name}`
2. To ensure the correct SSH key is used when connecting to Bitbucket, update or create your SSH configuration file (*~/.ssh/config*) with the following settings:
```config
Host bitbucket.org
	AddKeysToAgent yes
	IdentityFile ~/.ssh/{ssh-key-name}
```
Where `{ssh-key-name}` is the location of the _private_ key file once it has been added to the ssh-agent.
### Provide Bitbucket Cloud with your public key
To add an SSH key to your user account:

1. Select the **Settings** cog - on the top navigation bar.
- From the **Settings** dropdown menu, select **Personal Bitbucket settings**.
- Under **Security**, select **SSH keys**.
- Select **Add key**.
- In the **Add SSH key** dialog, provide a **Label** to help you identify which key you are adding. For example, *Work Laptop \<Manufacturer\> \<Model\>*. A meaningful label will help you identify old or unwanted keys in the future.
- Open the _public_ SSH key file (public keys have the .pub file extension) in a text editor. The public key should be in the *.ssh/* directory of your user (or home) directory. The contents will be similar to:
```
 ssh-ed25529 LLoWYaPswHzVqQ7L7B07LzIJbntgmHqrE40t17nGXL71QX9IoFGKYoF5pJKUMvR+DZotTm user@example.com   
```
2. Copy the contents of the _public_ key file and paste the key into the **Key** field of the **Add SSH key** dialog.
3. Select **Add key**.
    - If the key is added successfully, the dialog will close and the key will be listed on the **SSH keys** page.
    - If you receive the error That SSH key is invalid, check that you copied the entire contents of the _public_ key (.pub file).
### Check that your SSH authentication works
To test that the SSH key was added successfully, open a terminal on your device and run the following command: `ssh -T git@bitbucket.org`

If SSH can successfully connect with Bitbucket using your SSH keys, the command will produce output similar to:
```
authenticated via ssh key.

You can use git to connect to Bitbucket. Shell access is disabled
```
