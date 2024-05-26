#git 
For git to ignore files we need to create `.gitignore` file, and define it's rules.
The `.gitignore` file should be placed at the root of your Git repository. This means it should be located in the top-level directory of your project, where the `.git` directory (the Git repository) is also located.
Any subdirectory could contain its own `.gitignore`.

### formatting rules:
- \<filename\>: git will ignore a specific file with this name
- pattern matching (RegEx): `* ? [aeiou] [0-9]`  
	example: `logs/*.txt`
- negative expressions: ignore all .php files except index.php:
	`*.php`
	`!index.php`
- ignore all files in a dir: 
	- `assets/videos/`
- Comments:
	- `# this is a comment`
- Blank lines are skipped

useful ignore templates from [github](https://github.com/github/gitignore)

#### ignore global files
user specific instead of repo specific
`git config --global core.excludesfile ~/.gitignore_global-filname`

#### ignore future changes to a file
To have a file in a repo in its initial state and ignore all **future** changes to it, do as follows:
1. [[commit]] the initial state of file as you want it to be saved to the repo.
2. add the file to .gitignore, to ignore all future changes to it.
3. [[Technology/Version_Control/Git/rm|remove]] the file from **index** by running the following command:
	`git rm --cached file_name`

### check which files are ignored:
To see whether a file is ignored by Git, you can use the [[status|git status]] command with the `--ignored` option: `git status --ignored`. This option will show both the tracked and untracked files that match the patterns specified in the `.gitignore` file 

If a file is listed under the "Ignored files" section, it means that it matches a pattern specified in the `.gitignore` file, and Git is intentionally not tracking it. Example output:
```vb
On branch master
Your branch is up to date with 'origin/master'.

Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
	modified:   tracked_file.txt

Ignored files:
  (use "git add -f <file>..." to include in what will be committed)
	untracked_file.txt
	build/
```
In this example, "untracked_file.txt" and the entire "build/" directory are ignored by Git based on the rules defined in the `.gitignore` file.

Keep in mind that using the `--ignored` option with `git status` is not necessary to check if a specific file is ignored. You can simply open the `.gitignore` file in the root of your repository and check if the file's name or its pattern is listed there. If it is listed, it means Git will ignore it. The `--ignored` option is more useful when you want to see a complete list of ignored files in the entire working directory.