#linux 
package manager for Debian

list specific package:   `dpkg -l <package_name>`
`-L, --listfiles` package-name...
	List files installed to your system from package-name.
	
sort packages by space usage [(source)](https://www.google.com/url?sa=t&rct=j&q=&esrc=s&source=web&cd=&ved=1ahUKEwi7_eK959v0AhWBYsAKHSmbADMQFnoECAsQAQ&url=https%3A%2F%2Funix.stackexchange.com%2Fquestions%2F40442%2Fwhich-installed-software-packages-use-the-most-disk-space-on-debian&usg=AOvVaw2gixurBZ6VpVBTDIKyRLRc):  
```shell
dpkg-query -Wf '${Installed-Size}\t${Package}\n' | sort -n
```

Installing .deb file:
`sudo dpkg -i package_file.deb`
	If `--recursive` or `-R` option is specified, package-file must refer to a directory instead.
	Installation consists of the following steps:
	  1. Extract the control files of the new package.
	  2. If another version of the same package was installed before the new installation, execute prerm script of the old package.
	  3. Run `preinst` script, if provided by the package.
	  4. Unpack the new files, and at the same time back up the old files, so that if something goes wrong, they can be restored.
	  5.  If another version of the same package was installed before the new installation, execute the `postrm` script of the old package. Note that this script is executed after
	  the `preinst` script of the new package, because new files are written at the same time old files are removed.
	  6. Configure the package. See `--configure` for detailed information about how this is done.

`--force-overwrite` overwrite a conflicting file. If during installation of several packages (by dependency) one file is being edited by different packages this option will force overwriting the file. Otherwise the last installation will fail.

information about .deb file:   `dpkg -I path_to_deb_file`
find out package apache-perl or sudo is installed or not, type command:
	`dpkg -s apache-perl`
recently installed packages:
	`zcat -f /var/log/dpkg.log* | grep "\ install\ " | sort`
remove a package:  `sudo dpkg -r <package_name>`,  \<package_name\> could be verified through [[apt-get]]:  `apt-cache show <package_name>`
purge a package: `sudo dpkg -P <package>`

### Architecture
Show native architecture: `dpkg --print-architecture`
Show all used architectures (which are allowed to be installed): `dpkg --print-foreign-architecture`
Show all packages: `dkpg --get-selections`. To see which use different arch then amd64 use as follows:`dpkg --get-selections | grep 386`, or `...|grep amhf`
