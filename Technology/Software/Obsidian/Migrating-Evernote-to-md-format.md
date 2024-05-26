#migration
1. In Evernote app (**desktop only**, not web or phone) export the note or notebook to *.enex* file.
2. Download the [evernote2md](https://github.com/wormi4ok/evernote2md/releases/latest) converter, extract.
3. Convert each *.enex* as follows: `evernote2md note.enex destFolder` or in batch: `evernote2md *.enex destFolder`
>In ver 0.18.1 extracting notebooks in batch '\*' doesn't work.
4. Then just move the *.md* files to Obsidian folder