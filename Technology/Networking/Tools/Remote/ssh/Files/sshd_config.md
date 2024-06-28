#ssh 
ssh system wide configuration file.
Located in */etc/ssh/*

Options:
`PermitRootLogin` *yes/no* prevents ssh users to login as root to this server.
`PasswordAuthentication` *yes/no* setting this to *no* will only allow logging in to server via [[ssh-keygen|ssh-key]].
> for the changes to take affect, restart the ssh service (*sshd* the ssh daemon): `sudo systemctl restart sshd`

