#bash 
one-line if-else statement checks if a file is executable:   `if [ -x fileName ]; then echo Yes; else echo No; fi`
- `-x`  [[conditional-expression]] check if file is executable

check if a string contains a substring:
```sh
STR='GNU/Linux is an operating system'
SUB='Linux'
if [[ "$STR" == *"$SUB"* ]]; then
  echo "It's there."
fi
```
the full string **has** to be to the left of the double-equal sign.

#### if - elif - else
```shell
#!/bin/bash

echo -n "Enter the first number: "
read VAR1
echo -n "Enter the second number: "
read VAR2
echo -n "Enter the third number: "
read VAR3

if [[ $VAR1 -ge $VAR2 ]] && [[ $VAR1 -ge $VAR3 ]]
then
  echo "$VAR1 is the largest number."
elif [[ $VAR2 -ge $VAR1 ]] && [[ $VAR2 -ge $VAR3 ]]
then
  echo "$VAR2 is the largest number."
else
  echo "$VAR3 is the largest number."
fi
```
