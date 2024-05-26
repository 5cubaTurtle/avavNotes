#python #IDE 

[official help](https://www.jetbrains.com/help/pycharm/)

## Keyboard Shortcuts
#### Search
Find actions (shortcut):   `Ctrl+Shft+A`
Find files:   `Ctrl+Shft+N`
Find string:   `Ctrl+Shft+F`

#### Navigation
[Source code navigation](https://www.jetbrains.com/help/pycharm/navigating-through-the-source-code.html)
jump to closing bracket:   `Ctrl`+`Shft`+`M`
center screen to cursor: `Ctrl`+`M`
roll screen up/down: `Ctrl`+`Up`/`Down`
jump to code block start/end:  `Ctrl`+`[`/`]`
mark code block to start/end:   `Ctrl`+`Shft`+`[`/`]`
jump to last edited code:   `Ctrl`+`Shft`+`Backspace`
jump to a variable/function under the caret:   `Ctrl`+`B` or `Ctrl`+`Click`
jump to a type under the caret:   `Ctrl`+`Shft`+`B`

##### Bookmarks
[use_bookmarks](https://www.jetbrains.com/help/pycharm/navigating-through-the-source-code.html#use_bookmarks)
bookmark dialog: `Shift+F11`
To create a bookmark with mnemonics, place the caret at the needed code line, press `Ctrl+F11` and select a number or a letter for the mnemonics.

#### Editing
move line up:   `Ctrl+Shft+Up`
toggle case for selected code:   `Ctrl+Shift+U`
[toggle column selection mode](https://www.jetbrains.com/help/pycharm/multicursor.html#toggle-between-normal-and-column-selection-modes): `Alt+Shft+Insert`

#### View
view toggler: `Ctrl`+`~`

#### Quick Info
to see function parameters move the caret between the parentheses and press `Ctrl+p`
class hierarchy:  `Ctrl+H`
call hierarchy: `Ctrl+Alt+H`

#### Code Generation
Override method of parent class: `Ctrl`+`o`

#### Settings
Change menu font size from [SO](https://stackoverflow.com/questions/39216427/how-to-increase-menu-and-tab-font-size-in-intellij-jetbrains-pycharm-phpstorm): 
	1.  `Settings/Preferences`
	2.  `Appearance & Behavior | Appearance`
	3.  Enable `Use custom font` option -- it will allow to change font used for GUI as well override its size.

scheme-changer sub-menu:``Ctrl+` `` (Ctrl+backtick)


### Debugging
Use non-suspending breakpoints. Select the expression that you want to log, hold *Shift*, and click the gutter at the line where the expression should be logged.
![[non-suspending-breakpoint.png]] 
configure to print the value of the specified variable:
![[brakepoing_print_value.png]]
