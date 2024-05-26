To see a list of tag files: `:set tags`
To set the tag file list, read the following help:
    `:help tags-option`
To add to tag file list:
To create a tags file: go to sources directory, then run `ctags -R`
To add to tags list: `:set tags += <path to tags file\>`
To see a stack of tags:  `:tags`
Jump to the tag underneath the cursor: `Ctrl`+`]`
Jump back up in the tag stack: `Ctrl`+`t`
Search for a particular tag: `:ts <tag> <RET>`
Go to the next definition for the last tag: `:tn`
Go to the previous definition for the last tag: `:tp`
List all of the definitions of the last tag: `:ts`