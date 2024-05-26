#linux 
apt provides a high-level commandline interface for the package management system. It is intended as an end user interface and enables some options better suited for interactive usage by default compared to more
       specialized APT tools like **apt-get**(8) and **apt-cache**(8).

### common operations
- install/upgrade a package:   `sudo apt install <package>`, this downloads *.deb* file to */var/cache/apt/archives* and installs it using [[dpkg]]. If the package already installed on the system, it will be upgraded to latest version. If a *.deb* file is given instead of a package name, it will install it.
	- `--only-upgrade`   will not install new packages
	- `-s, --dry-run`   will not perform any action
	- `-y, --yes`  Automatic yes to prompts, to run non-interactively (script).
	- install specific version:   `sudo apt-get install <package>=<version> -V`
		-`-V`  verbose
- remove: `apt remove <package>`
- purge: `apt purge <package>`
	- `purge` removes configuration files in `/etc` folder, `remove` will not. Files in `/home/*` will not be removed either way. [askUbuntu](https://askubuntu.com/a/231568), [itsfoss](https://askubuntu.com/a/231568)
- install a specific version of a package: `sudo apt install package_name=package_version`
- update: `sudo apt update`, will update the [[apt-cache|cache]] at */var/lib/apt/list/*.
- upgrade: `sudo apt upgrade`
	- Note that `full-upgrade` is used in preference to a simple `upgrade`, as it also picks up any dependency changes that may have been made.

### upgrading the kernel
After `apt update`, run `apt upgrade`. In most cases, running `sudo apt upgrade` is sufficient for regular package upgrades and kernel updates. However, if you encounter any complex dependency issues or need to handle system-wide changes during the upgrade, `sudo apt-get dist-upgrade` can be useful.

### archives
- download packages without installing: `apt install -d <package>`, or `--download-only`. This will download the deb file into */var/cache/apt/archives/*. 
- remove downloaded debs from */var/cache/apt/archives/*: `apt clean`

### info
- list all available versions of a package`apt list --all-versions package_name`
- list all installed packages:   `apt list --installed`
	- `-a`,` --all-versions`  list all versions
- show info about a package:   `apt show <package name>`
- search for a package with a similar name:`apt search qt-designer`

### apt-mark
- prevent Linux to update specified packages:
```shell
sudo apt-mark hold linux-generic linux-headers-generic linux
```
- to back allow updates to these packages use `unhold` instead of `hold`

### apt-rdepends
A tool to see dependencies of dependencies
```shell
sudo apt install apt-rdepends
```
you can see what other packages depend on a certain package.
```shell
apt-rdepends -r package_name
```

## troubleshooting 
>  dpkg: error processing /var/cache/apt/archives/.....deb (--unpack):
> trying to overwrite '....some file.....', which is also in package ....some other package...

A package overwriting a file of it's dependency is a problem in it self, but to workaround this:
go to */var/cache/apt/archives/* and install the package using [[dpkg]] `--force-overwrite` option. This solution is taken from [SO](https://askubuntu.com/q/176121)

### Warning
#### [repository 'xxx' doesn't support architecture 'yyy'](https://askubuntu.com/questions/741410/skipping-acquire-of-configured-file-main-binary-i386-packages-as-repository-x)
I tracked down offending repo (any for Google chrome in this dir)
```
cd /etc/apt/sources.list.d
grep chrome * | grep -v amd64
```
or more generally
```
grep -r google  /etc/apt | grep -v amd64 
```
Now do same as below for each repo file which matches above
```
cat /etc/apt/sources.list.d/google-chrome-unstable.list

### THIS FILE IS AUTOMATICALLY CONFIGURED ###
# You may comment out this entry, but any other modifications may be lost.
deb http://dl.google.com/linux/chrome/deb/ stable main
```
SOLUTION : limit to just 64 bit by introducing the [arch=amd64]
```
deb [arch=amd64] http://dl.google.com/linux/chrome/deb/ stable main
```
