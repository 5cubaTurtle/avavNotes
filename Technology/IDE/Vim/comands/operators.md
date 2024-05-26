`:help operator`

`c` change
`d` delete
`y` yank into register
`~`  swap case (only if *tildeop* is set)
`g~` swap case
`gu` make lowercase
`gU` make uppercase
`zf` define a [[fold]]

#### Deletion usage
`dd` or `ndd` Delete n lines to general buffer
`dw` Delete word to general buffer
`dnw` Delete n words
`d)` Delete to end of sentence
`db` Delete previous word
`D` Delete to end of line
`x` Delete character

#### frequent operations
`yy` or `Y` Yank (copy) line to general buffer
`“z6yy` Yank 6 lines to buffer z
`yw` Yank word to general buffer
`“a9dd` Delete 9 lines to buffer a
`“A9dd` Delete 9 lines; Append to buffer a
`J` Join lines. This essentially removes the immediate [[new-line]] character
Copy lines 30-60 from *old* to *new* file: `vi old`, `:30,60w new`
`:w` write work buffer
`:e <filename>` edit new file. Without `<filename>` this will reload current file
`p` Put general buffer after cursor
`P` Put general buffer before cursor
