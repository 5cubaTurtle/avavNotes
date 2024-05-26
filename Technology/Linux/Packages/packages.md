---
title: "Package Managment"
tags: "linux"
---
### installing Codelite on mint
Add the CodeLite public key to avoid warnings or worse from apt/aptitude
	`sudo apt-key adv --fetch-keys http://repos.codelite.org/CodeLite.asc`
Now let apt know that the repositories exist by adding the proper line to /etc/apt/sources.list. To do it use:
	`sudo apt-add-repository 'deb https://repos.codelite.org/ubuntu/ bionic universe'`
You then need update your repositories:
	`sudo apt-get update`
You can see which versions are available by doing:
	`apt-cache madison codelite`
Then do for example:
	`sudo apt-get install codelite=9.1*`
Per the codelite documentation, if you have an older version of codelite installed, remove it first, like so:
    `sudo apt-get purge codelite codelite-plugins`
The following commands will install the latest codelite on Ubuntu:
	sudo apt-key adv --fetch-keys http://repos.codelite.org/CodeLite.asc
	sudo apt-add-repository "deb http://repos.codelite.org/ubuntu/ $(lsb_release -sc) universe"
	sudo apt-get update
	sudo apt-get install codelite wxcrafter
To fix dependencies:
	sudo apt-get -f install
