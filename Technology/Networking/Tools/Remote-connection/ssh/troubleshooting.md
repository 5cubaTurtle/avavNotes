#ssh 

Error: "Please make sure you have the correct access rights and the repository exists"
try these 2 [solutions](https://stackoverflow.com/questions/25927914/git-error-please-make-sure-you-have-the-correct-access-rights-and-the-reposito/51820472#51820472):
1. update the url of the repository:
```shell
git remote set-url origin git@github.com:username/repository.git
```
2. add the ssh-key to ssh-agent:
start the agent:   `eval "$(ssh-agent -s)"`
Agent pid 5867
add the private key:  `ssh-add <private-ssh-key-file-name>` // eg. id_rsa (not `.pub`)

##### key conflict:
	Warning: the ECDSA host key for 'plc2-0-007' differs from the key for the IP address '192.168.88.15'
	Offending key for IP in /home/ava/.ssh/known_hosts:133
	Matching host key in /home/ava/.ssh/known_hosts:137
	Are you sure you want to continue connecting (yes/no)? no
	Host key verification failed.

remove the "offending key" line from known_hosts using [[sed]]:
```shell
sed -i '133d' ~/.ssh/known_hosts
```
instead of '137', use the line number from your case.

###### WARNING: POSSIBLE DNS SPOOFING DETECTED!
	@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
	@       WARNING: POSSIBLE DNS SPOOFING DETECTED!          @
	@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
	The ECDSA host key for plc2-0-005 has changed,
	and the key for the corresponding IP address 192.168.88.36
	is unknown. This could either mean that
	DNS SPOOFING is happening or the IP address for the host
	and its host key have changed at the same time.
	@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
	@    WARNING: REMOTE HOST IDENTIFICATION HAS CHANGED!     @
	@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
	IT IS POSSIBLE THAT SOMEONE IS DOING SOMETHING NASTY!
	Someone could be eavesdropping on you right now (man-in-the-middle attack)!
	It is also possible that a host key has just been changed.
	The fingerprint for the ECDSA key sent by the remote host is
	SHA256:cDG8UdlSPQrk/k1TvmIGFy0SWfJxD0fWzYgi4NOz0Q0.
	Please contact your system administrator.
	Add correct host key in /home/ava/.ssh/known_hosts to get rid of this message.
	Offending ECDSA key in /home/ava/.ssh/known_hosts:13
	  remove with:
	  ssh-keygen -f "/home/ava/.ssh/known_hosts" -R "plc2-0-005"
	ECDSA host key for plc2-0-005 has changed and you have requested strict checking.
	Host key verification failed.
As suggested by the warning, you could try the [[ssh-keygen]] command: 
`ssh-keygen -f "/home/ava/.ssh/known_hosts" -R "<hostname>"`
