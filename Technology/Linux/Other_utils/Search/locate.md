Find files by name
quickly find files on the filesystem based on their name mlocate is a new implementation of locate, a tool to find files anywhere in the filesystem based on their name, using a fixed pattern or a regular expression. Unlike other tools like [[find]](1), locate uses a previously created database to perform the search, allowing queries to execute much faster. This database is updated periodically from [[crontab|cron]].
>[!Remember]
>[[#Database|Update]] the DB if you can't find a file

Options:
- `-i`, `--ignore-case`
- `-c`,`--count` only display the number of matching entries.
- `-b`, `--basename` Match only the base name against the specified patterns.  This is the opposite of `--wholename`.
- `-q` suppress errors
- `-S` show statistics

Search only in specific folder: `locate /home/ava/*su.md`
	This will search for `su.md` in */home/ava/*.

To search for a file named exactly NAME (not *NAME*), use: 
```sh
locate -b '\NAME'
```
Since *\\* is a globbing character, it disables the implicit replacement of NAME by \*NAME\*.

For long search results do: `locate <pattern>|less`
## Database
#### updating DB
`sudo updatedb` this is a link to the correct DB version.
>[!locate version]
There are 3 different forks for *locate* out there. To determine yours use [[which]]: `which locate`
Update *mlocate* database: `sudo updatedb.mlocate`
Update *plocate* database: `sudo updatedb.plocate`
There is also the old plain *locate*.
#### creating separate DB
This will create your local database only for the specific directory (`MyFolder`).
```
updatedb -o ~/tmp.db -l0 -U MyFolder
locate   -d ~/tmp.db "foo"
```
This will create a separate database for a the specifies folder.
