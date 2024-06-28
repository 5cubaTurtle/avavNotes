An interface to the system reference manuals

`man man`

read a page from specific section: `man 5 passwd` - read the entry `passwd` from the section `5` (File formats).

[[apropos]]: `man -k <keyword>`
[[whatis]]: `man -f <man_page>`

Read a *.gz* document: `man -l README-P2P.gz`
- `-l` read the provided file (i.e.`README-P2P.gz`). If given `-` as a filename, [[stdin]] will be taken as input (i.e. `cat README-P2P.gz | man -l -`).
