#git
Get and set repository or global options

File locations:
	System (`--system`): `/etc/gitconfig`  (not present currently)
	User (`--global`): `~/.gitconfig`
	Project (default): `my_project/.git/config`
1. example user configuration file: *~/.gitconfig*:
	```gitconfig
	email = avner.averman@bladeranger.com
	name = Avner A
	```
	1. changing config: `git config [flags] <option>`
		- default is the Project level config
		- `--system`   System level config
		- `--global`  User level config
		- `--list, -l`   List all configs
		1. Change editor:   `git config --global core.editor "vim"`
		2. Change Git user name by running: `git config --global user.name “Your Name”`
		3. Change Git user email by running: `git config --global user.email “name@email.com”`

### default log behavior
From [SO answer](https://stackoverflow.com/a/63500739) to change the default [[log|git log]] command:
```shell
git config --global --add format.pretty "%C(yellow)%h%Creset%x09%Cred%<(13)%an%Creset%x09%Cblue%ad%Creset%x09%s"
```
- `--add`   add a configuration
- `--unset`   remove a configuration

A named format is added with:
```shell
git config --global pretty.dateline "format:%C(yellow)%h%Creset%x09%Cred<(13)%an%Creset%x09%Cblue%ad%Creset%x09%s"
```

### Using a git alias
In order to create a new git alias, use the `git config` command and define a new alias named “pushd”
```shell
git config --global alias.pushd "push -u origin HEAD"
```
When you are done adding and committing fiels to your repository, set the upstream branch using your newly defined alias.
```shell
git pushd
Total 0 (delta 0), reused 0 (delta 0)
 * [new branch]      HEAD -> branch
Branch 'branch' set up to track remote branch 'branch' from 'origin'.
```
