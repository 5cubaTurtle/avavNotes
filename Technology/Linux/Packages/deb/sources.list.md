[itsFoss guide](https://itsfoss.com/sources-list-ubuntu/)
The APT package manager gets the repository information from the */etc/apt/sources.list* file and files listed in */etc/apt/sources.list.d* directory. Repository information is usually in the following format:
```sh
archive-type [arch-type] repository-url distribution component
```

Example:
```sh
deb http://us.archive.ubuntu.com/ubuntu/ bionic main
```

- `archive-type`: *deb* or *deb-sr* which is the source code.
- `[arch-type]` optional architecture type. For example: `[arch=amd64]` for 64bit. If none present then multi architecture will be a candidate, i.e. `apt update` will try other architectures as in `dpkg --print-foreign-architectures`
- `repository-url`: could be visited by using a browser to observe the repository's directory structure.
- `distribution`: in the tree structure of the repository it is one of the distributions from the **dists** directory.
- `component` is one of the five types of default Ubuntu repositories; `main`, `restricted`, `multiverse`, `universe` or `by-hash`.

You can combine more than one (if available) in the same line, actually. Instead of writing two lines like this:
```sh
deb http://archive.ubuntu.com/ubuntu impish main
deb http://archive.ubuntu.com/ubuntu impish restricted
```
You write two of them together like this:
```sh
deb http://archive.ubuntu.com/ubuntu impish main restricted
```

When [[apt]] update command ran, the apt package manager gets the information about the available packages (and their version info) from the repositories and stores them in local cache of metadata in the */var/lib/apt/lists* directory. The [[apt-cache]] command queries this local APT cache.

#### sources.list.d directory
*sources.list* file is for the official Ubuntu repositories.  For any external repositories and PPA, you add a *.list* file (with the repository details) in this *sources.list.d* directory:
![[sources.list.d-example.png]]
The external repositories can be easily disabled by editing the corresponding *.list* file in the *sources.list.d* direcotry. This could be done by adding `#` in front of the repository details or by removing its corresponding *.list* file.

see specific source of packages:   `cat /etc/apt/sources.list.d/bladeranger.list`
