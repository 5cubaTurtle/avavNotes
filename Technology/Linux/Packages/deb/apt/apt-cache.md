#linux 
query the APT cache

[itsFOSS explanation](https://itsfoss.com/apt-cache-command/)
The [[apt]]-update command 
The **location of APT cache** is */var/lib/apt/lists/*. it contains text files with metadata and other data like icons (maybe for GUI package manager like the [[ubuntu-software]]) as *tar.gz* files:
```sh
archive.ubuntu.com_ubuntu_dists_jammy-updates_universe_binary-amd64_Packages
archive.ubuntu.com_ubuntu_dists_jammy-updates_universe_dep11_icons-48x48.tar.gz
```

Which repository metadata to cache depends on the repositories added in your source list in the `/etc/apt/sources.list` file and additional repository files located in `/etc/apt/sources.list.d` directory.

Surprisingly, apt-cache doesn’t clear the APT cache. For that you’ll have to [use the `apt-get clean` command](https://itsfoss.com/clear-apt-cache/).

## usage examples:
Search package lists for the *reprepro* package: `apt-cache search reprepro`, it looks for the search term in both the name and description of the package.
- `--name-only` narrow down your search to look for the search term in package names only.
- `--full` display complete details of all the matched packages.

Show details of a package: `apt-cache show <package>`

Displays information about the package name, version and its forward and reverse dependencies: `apt-cache showpkg <package>`

### apt-cache policy
`apt-cache policy cowsay`
For debugging the issue related to the [preference file](https://debian-handbook.info/browse/stable/sect.apt-get.html?ref=itsfoss.com#sect.apt.priorities).

Specifying the package name will show whether the package is installed, which version is available from which repository and its priority.

### dependencies
You can [check the dependencies of a package](https://itsfoss.com/check-dependencies-package-ubuntu/) before (or even after) installing it. It also shows all the possible packages that can fulfill the dependency:
`apt-cache depends <package>`

check which packages are dependent on a certain package by checking the reverse dependencies with apt-cache:  `apt-cache rdepends <package>`

You may get troubled with [unmet dependencies issue in Ubuntu](https://itsfoss.com/held-broken-packages-error/) or other Linux. The apt-cache command provides the option to check all the unmet dependencies of various available packages on your system: `apt-cache unmet`
