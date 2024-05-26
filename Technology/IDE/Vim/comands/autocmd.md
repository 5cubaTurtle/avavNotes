help page at `:h 40.3`
[SO answer](https://stackoverflow.com/a/28310179)
An auto-command is a command that is executed automatically in response to some event, such as a file being read or written or a buffer change.

For example, map the *F4* key to compile and run if the file type is *.cpp*:
```sh
autocmd filetype cpp nnoremap <F4> :w <bar> exec '!g++ '.shellescape('%').' -o '.shellescape('%:r').' && ./'.shellescape('%:r')<CR>
```

To get the name of a specific key, for example `<F4>` see [[Technology/IDE/Vim/Colon-cli/help#Getting the code of the key in <> form|help]]
