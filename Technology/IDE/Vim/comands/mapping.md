The mapping go into the .vimrc file
- to resource the .vimrc during a running session: `:so $MYVIMRC`
[guide](https://alldrops.info/posts/vim-drops/2018-05-15_understand-vim-mappings-and-create-your-own-shortcuts/), [another guide](https://dev.to/iggredible/basic-vim-mapping-5ahj)
### Syntax:
map-commad map-argument {lhs} {rhs}
For example:
```
nnoremap <silent> ,<space> :nohlsearch<CR>
```
#### map-command
`map-command` defines:
- whether you’re **adding new/removing/listing** map
- whether the mapping will be **recursive/non recursive**
- the **mode** where the mapping will be applied

From the example:
`nnoremap` defines that this is **adding a new mapping** to be apllied in `NORMAL` **mode** and it’s **non recursive** .
#### map-arguments
t’s **optional** and it must appear right after the **map-command**, you can use one or more arguments combined, and they can be used in any order.
From the example:
`<silent>` defines that when you execute this mapping pressing `,<space>` , the command `:nohlsearch` will not be echoed on the command line.
#### `{lhs}` left-hand-side
That’s where you define the shortcut or the key(s) you’re gonna use. It can be a single key like `,` or a sequence of keys like `,<space>`.
From the example:
`,<space>` is the shortcut, it’s the sequence of keys that calls what you defined on `{rhs}`.
#### `{rhs}` right-hand-side
That’s where you define what will your shortcut replace/execute when you press the key(s) defined at `{lhs}`. It can replace a key or execute a sequence of keys, it can call vim native commands (like previous example) or functions you created on vimscript language, things can be as complex as you wish.
From the example:
`:nohlsearch<CR>` is what will be executed, vim will type `:nohlsearch` followed by the `<Enter>` key that is defined by `<CR>`.

### Examples
```yaml
" save the file, compile with g++ then run
nnoremap ,br :w<CR> :!g++ % -o %:r && ./%:r<CR>

" if file type is .py(python) and F4 was pressed then save and run
autocmd filetype python nnoremap <F4> :w <bar> exec '!python '.shellescape('%')<CR>

" if file type is .c and F4 is pressed, the save, compile and execute
autocmd filetype c nnoremap <F4> :w <bar> exec '!gcc '.shellescape('%').' -o '.shellescape('%:r').' && ./'.shellescape('%:r')<CR>

" if file type is .cpp and F4 is pressed, the save, compile and execute
autocmd filetype cpp nnoremap ,r :w <bar> exec '!g++ '.shellescape('%').' -o '.shellescape('%:r').' && ./'.shellescape('%:r')<CR>

" c++ comment out the current line 
nnoremap <c-j> 0i//<esc>j
```

```yaml
" compile and run
autocmd filetype python nnoremap <F4> :w <bar> exec '!python '.shellescape('%')<CR>
autocmd filetype c nnoremap <F4> :w <bar> exec '!gcc '.shellescape('%').' -o '.shellescape('%:r').' && ./'.shellescape('%:r')<CR>
autocmd filetype cpp nnoremap <F4> :w <bar> exec '!g++ '.shellescape('%').' -o '.shellescape('%:r').' && ./'.shellescape('%:r')<CR>
autocmd filetype cpp nnoremap ,br :w<CR> :!clang++-18 -lstdc++ -Wall -Wextra % -o %:r && ./%:r<CR>

""" C++
" Comment this line
autocmd filetype c,cpp nnoremap <c-j> 0i//<esc>j
" Print this word
autocmd filetype cpp nnoremap cout yeo<tab>cout << "<c-r>": "<< <c-r>" << endl;<esc>2B
autocmd filetype cpp nnoremap ,ios i#include <iostream><enter>using std::cout, std::endl;
" Closing brackets autocompletion
autocmd filetype c,cpp inoremap {<c-j> {<CR>}<Esc>ko<tab>
autocmd filetype c,cpp inoremap {} {   }<esc>2hi
"autocmd filetype c,cpp inoremap () ()<esc>i
autocmd filetype c,cpp inoremap ()<c-j> () {<CR>}<Esc>ko<tab>
autocmd filetype c,cpp inoremap [] []<esc>i
autocmd filetype c,cpp inoremap #inc #include <><esc>i

" Insert a single character
nnoremap <space> i <esc>r
```

[[vimrc|This]] is my *.vimrc* file.
### Other
Display user defined mappings: `:map`
To get the name of a specific key, for example `<F4>` see [[Technology/IDE/Vim/Colon-cli/help#Getting the name of the key|Getting the code of the key]].
