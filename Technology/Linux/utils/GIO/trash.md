#GIO
trash \[OPTION...\] \[LOCATION...\]
Sends files or directories to the ‘Trashcan’. This can be a different folder depending on where the file is
located, and not all file systems support this concept. In the common case that the file lives inside a 
user’s home directory, the trash folder is \$XDG_DATA_HOME/Trash (ubuntu 20.04:`$HOME/.local/share/Trash`).

Note that moving files to the trash does not free up space on the file system until the ‘Trashcan’ is emptied. If you are interested in deleting a file irreversibly, see the remove command.
Inspecting and emptying the ‘Trashcan’ is normally supported by graphical file managers such as Nautilus.

trashing a file:   `gio trash <file_name>`
list contents of trash:  `gio list trash://`

Options
`-f, --force` Ignore non-existent and non-removable files.
`--empty` Empty the trash.
