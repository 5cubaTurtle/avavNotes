Let's say I have code in the directory *~/local_dir/myNewApp*,
 and I want to put it under https://svn.host/existing_path/myNewApp
 (while being able to ignore some binaries, vendor libraries, etc.).

- Create an empty folder in the repository svn mkdir https://svn.host/existing_path/myNewApp
- Go to the parent directory of the project: `cd ~/local_dir`
- Check out the empty directory over your local folder.
	Don't be afraid - the files you have locally will not be deleted.
	`svn co https://svn.host/existing_path/myNewApp`. If your folder has a different name
	locally than in the repository, you must specify it as an additional argument:
	`svn co https://svn.host/existing_path/myNewApp ~/local_dir/localNameOfFolder`
- You can see that svn st will now show all your files as `?`, which means that they are not currently under revision control. 
- Perform `svn add` on files you want to add to the repository, and add others to svn:ignore. You may find some useful options with svn help add, for example --parents or --depth empty, when you want selectively add only some files/folders. 
- Commit with `svn ci`