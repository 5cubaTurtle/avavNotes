#shell 

changing the terminal title in 2 ways:
- by [[echo]]: `echo -ne "\033]0;new_title\007"`
The `\007` is octal for 7 equivalent  to `\a`. And `\033` is equivalent to `\e`. Thus we could also use: `echo -ne "\e]0;new_title\a"`
The previous method works as long as *PS1*  does not contain the ending which will be presented in the next method.
- through *PS1* [[prompting|environment variable]]: `PS1=$PS1"\[\e]0;new_title\a\]"`
	- notice that we have to add to the end of *PS1* the string `"\[\e]0;new_title\a\]"`, once we do that, the previous method, using [[echo]], will stop working.

To remove the title simply leave it blank: `echo -ne "\e]0;\a"`

To set the title to *user@hostname* and *current working directory*: 
`PS1='\[\e]0;\u@\h: \w\a\]${PS1}'`


Also, to change the title: `PS1='\[\e]2;My Terminal\a\]'$PS1`
In the escape sequence `\[\e]2;` in the `PS1` variable, the `2` is an argument passed to the `\e]` escape sequence. This argument is used to specify the type of terminal window title that is being set.

In this case, the argument `2` is used to set the title of the terminal window. It tells the terminal emulator that the text following this argument is the title of the terminal window. The terminal emulator will interpret this and set the title accordingly.

There are other types of window title that can be set with different arguments, such as `0` which is used to set the window icon name, and `1` which is used to set the icon title.

It's important to note that the escape sequences and arguments used to set the terminal title might vary depending on the terminal emulator you are using. The mentioned escape sequence is a common one, but it may not work for all terminal emulators.

