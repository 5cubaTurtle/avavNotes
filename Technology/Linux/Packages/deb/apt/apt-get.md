#linux 
command-line tool for handling packages

- Install a package:   `apt-get install <package_name>`
	- `-y` Automatic *yes* to prompts. [[#configuration]] Item: *APT::Get::Assume-Yes*.
	 - `--reinstall` will force reinstall already up-to-date packageskj
- add repository: `sudo add-apt-repository ppa:cartes/drawing`
	This will add the file *cartes-ubuntu-drawing-focal.list* to the folder: */etc/apt/sources.list.d*. This will make `apt update` search in the *cartes/drawing* repo for updates.

##### info
- Show dependencies of a package:   `apt-cache depends package_name`
- Get more info about a <package\>
	`apt-cache show <package>`
- search for available packages by name (probably searches localy, no need for internet)
	`apt-cache search <name_of_the_package> `

##### configuration
Use this apt option to turn warnings into errors:
```shell
apt-get update -o APT::Update::Error-Mode=any
```
- `-o APT::Update::Error-Mode=any`  any warning will become error (good for scripting if you want catch errors)
- `-o Dir::Etc::sourcelist="sources.list.d/bladeranger.list"`  update from specified source.list. See [[update_robot|example]]