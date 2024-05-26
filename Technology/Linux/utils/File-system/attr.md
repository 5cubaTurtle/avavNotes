#linux 
extended attributes on filesystem objects (files or folders)


list all attributes of *workspace.json*: `attr -l workspace.json`
set the *.git* folder to be ignored by [[Dropbox]] listener: 
	`attr -s com.dropbox.ingnored -V 1 .git`
remove an attribute of the file *workspace.json*:
	`attr -r com.dropbox.ingnored workspace.json` 