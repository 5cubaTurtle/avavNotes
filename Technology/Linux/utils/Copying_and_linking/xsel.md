#copy 
manipulate the X selection

copy the contentents of id_rsa.pub to clipboard using [[xclip]]:  
	`cat ~/.ssh/id_rsa.pub | xclip -sel clip`  
using xsel you can shove your clipboard into a new file:  
	`xsel -o > out.txt`