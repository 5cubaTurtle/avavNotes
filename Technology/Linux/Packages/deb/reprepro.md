#linux 
produce, manage and sync a local repository of Debian packages

list available debs in a distro: `reprepro list <distro>`
list package locations: `reprepro dumpreferences`

add *mypack.deb* package to *mydistro* distribution:`reprepro includedeb mydistro mypack.deb`
or batch include all deb files in a dir: `reprepro includedeb mydistro *.deb`
remove a package from a distro:`reprepro remove mydistro mypackage`
- `-A` remove specific architecture:` reprepro -A amd64 remove mydistro mypackage`
- `-b <path/to/repository>` will override the [[#REPREPRO_BASE_DIR]] default path to repo.

[setup guide](https://www.virtono.com/community/tutorial-how-to/create-your-own-apt-repository-with-reprepro-on-ubuntu/)
[debian guide](https://wiki.debian.org/DebianRepository/SetupWithReprepro)

#### REPREPRO_BASE_DIR
This *env* variable will determine the default path to repository to operate upon in all *reprepro* commands.

#### apt metadata
This is the index files in *dists* folder. These are the *Release*/*Packages*/*Sources* files.
To create a link to a distro: define the *Suite* field in the *conf/distributions* file and then run: `reprepro createsymlinks`. This will make the a link with the Suite to the distro. For example:
in the follwoing *distributions* file:
```reprepro
Origin: Blade Ranger Pleco
Label: Blade Ranger Pleco
Suite: stable
Codename: focal-stable
Architectures: armhf arm64
Components: main
Description: A new(Dec14,2022) Apt repository for Blade Ranger Pleco
SignWith: 6368E30D

Origin: Blade Ranger Pleco
Label: Blade Ranger Pleco
Suite: testing
Codename: focal-testing
Architectures: armhf arm64
Components: main
Description: A new(Dec14,2022) Apt repository for Blade Ranger Pleco
SignWith: 6368E30D
```
*Suite: stable* and *Suite: testing* , after executing `reprepro createsymlinks`:
![[suit-symlink.png]]
so we can use these names instead of the distros names: `reprepro list stable`

#### Editing the distribution
If adding architecture to the *conf/distributions* file, or adding a new deb file,
export the new change: `reprepro export <distro>` 

If removing architecture from the *conf/distributions* file: `reprepro -V --delete clearvanished`, this will apply the change to the database. The `--delete` option will also delete the actual package .deb file from the *pool* folder. The index files in *dists* folder are not removed automatically.

#### TODO:
Deleting files just added to the pool but not used.
(to avoid use --keepunusednewfiles next time)
- see how to keep older versions of packages
- generate gpg from local machine build and sign packages local and send them to reprepro for better safety.
- use Suite for shortcut to stable/testing (need to change the Codename from stable/testing) see [this guide](https://www.virtono.com/community/tutorial-how-to/create-your-own-apt-repository-with-reprepro-on-ubuntu/). Section "Include packages"

#### Setup guide from chatGPT
To set up a reprepro repository, you will need to do the following:
1.  Install the reprepro package on your system.
2.  Create a directory where you want to store your repository, and make sure that it has the appropriate permissions.
3.  Create a configuration file called `distributions` in the repository directory. This file will define the distributions that your repository will contain.
4.  Create a subdirectory called `conf` in the repository directory.
5.  In the `conf` directory, create a file called `options` that contains any options that you want to apply to the repository as a whole.
6.  Use the `reprepro` command to import packages into the repository.
7.  Configure your package manager to use your repository, so that users can install packages from it.

Here is an example of a `distributions` file:

```reprepro
Origin: My Repository
Label: My Repository
Codename: stable
Architectures: i386 amd64
Components: main
Description: My personal package repository
```

In this example, the repository is called *My Repository*, and it contains packages for the *i386* and *amd64* architectures in a distribution called "*stable*".

The `options` file can contain any options that you want to apply to the repository as a whole. For example, you could use it to specify the GPG key that you want to use to sign your packages, or to specify which components of the repository should be included when users update their package lists.

Once you have set up your repository, you can use the `reprepro` command to import packages into it. For example, to import a package called `mypackage.deb`, you would run the following command:
`reprepro -b /path/to/repository includedeb stable /path/to/mypackage.deb`

This would import the `mypackage.deb` package into the `stable` distribution of your repository.

Finally, you will need to configure your package manager to use your repository, so that users can install packages from it. The exact steps for doing this will depend on the package manager that you are using, but generally you will need to add the repository's URL to your package manager's list of package sources.
