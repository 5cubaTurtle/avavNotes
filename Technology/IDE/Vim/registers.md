Vim provides registers associated with each letter to save buffers of text in them or other things like [[Technology/IDE/Vim/comands/macros|macros]].

Display the registers: `:reg[isters]`
- `"xy` yank into register x
- `"xp` paste contents of register x
- `"+y` yank into the system clipboard register
- `"+p` paste from the system clipboard register

> [!NOTE]
Registers are being stored in *~/.viminfo*, and will be loaded again on next restart of vim.
#### Special registers:
`0` last yank
`"` unnamed register, last delete or yank
`%` current file name
`#` alternate file name
`*` clipboard contents (X11 primary)
`+` clipboard contents (X11 clipboard)
`/` last search pattern
`:` last command-line
`.` last inserted text
`-` last small (less than a line) delete
`=` expression register
`_` black hole