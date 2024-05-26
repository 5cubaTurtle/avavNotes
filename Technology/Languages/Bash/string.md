#shell 

[linuxize guide](https://linuxize.com/post/how-to-compare-strings-in-bash/)

When comparing strings in Bash you can use the following operators:

`string1 = string2` and `string1 == string2` - The equality operator returns true if the operands are equal.
	-   Use the `=` operator with the `test` `[` command.
	-   Use the `==` operator with the `[[` command for pattern matching.
`string1 != string2` - The inequality operator returns true if the operands are not equal.
`string1 =~ regex`- The regex operator returns true if the left operand matches the extended regular expression on the right.
`string1 > string2` - The greater than operator returns true if the left operand is greater than the right sorted by lexicographical (alphabetical) order.
`string1 < string2` - The less than operator returns true if the right operand is greater than the right sorted by lexicographical (alphabetical) order.
`-z string` - True if the string length is zero.
`-n string` - True if the string length is non-zero.

-   A blank space must be used between the binary operator and the operands.
-   Always use double quotes around the variable names to avoid any word splitting or globbing issues.
-   Bash does not segregate variables by “type”, variables are treated as integer or string depending on the context.

##### [Check if Two Strings are Equal](https://linuxize.com/post/how-to-compare-strings-in-bash/#check-if-two-strings-are-equal)

```sh
#!/bin/bash

if [ "$VAR1" = "$VAR2" ]; then
    echo "Strings are equal."
else
    echo "Strings are not equal."
fi
```

Here is another script that takes the input from the user and compares the given strings. In this example, we will use the `[[` command and `==` operator.
```sh
#!/bin/bash

read -p "Enter first string: " VAR1
read -p "Enter second string: " VAR2

if [[ "$VAR1" == "$VAR2" ]]; then
    echo "Strings are equal."
else
    echo "Strings are not equal."
fi
```

You can also use the logical and `&&` and or `||` to compare strings:
```sh
[[ "string1" == "string2" ]] && echo "Equal" || echo "Not equal"
```

##### Check if a string contains a substring:
One approach is to use surround the substring with asterisk symbols `*` which means match all characters.
```sh
#!/bin/bash

VAR='GNU/Linux is an operating system'
if [[ $VAR == *"Linux"* ]]; then
  echo "It's there."
fi
```

Another option is to use the regex operator `=~` as shown below:
```sh
#!/bin/bash

VAR='GNU/Linux is an operating system'
if [[ $VAR =~ .*Linux.* ]]; then
  echo "It's there."
fi
```
The period followed by an asterisk `.*` matches zero or more occurrences any character except a newline character.

##### [Check if a String is Empty](https://linuxize.com/post/how-to-compare-strings-in-bash/#check-if-a-string-is-empty)
Check whether a variable is an empty string or not by using the `-n` and `-z` operators.
```sh
#!/bin/bash

VAR=''
if [[ -z $VAR ]]; then
  echo "String is empty."
fi
```

##### Comparing Strings with the Case Operator
Instead of using the test operators you can also use the [case statement](https://linuxize.com/post/bash-case-statement/) to compare strings:
```sh
#!/bin/bash

VAR="Arch Linux"

case $VAR in
  "Arch Linux")
    echo -n "Linuxize matched"
    ;;

  Fedora | CentOS)
    echo -n "Red Hat"
    ;;
esac
```

##### Lexicographic Comparison
Lexicographical comparison is an operation where two strings are compared alphabetically by comparing the characters in a string sequentially from left to right. This is rarely used.

The following scripts compare two strings lexicographically:
```sh
#!/bin/bash

VAR1="Linuxize"
VAR2="Ubuntu"

if [[ "$VAR1" > "$VAR2" ]]; then
    echo "${VAR1} is lexicographically greater then ${VAR2}."
elif [[ "$VAR1" < "$VAR2" ]]; then
    echo "${VAR2} is lexicographically greater than ${VAR1}."
else
    echo "Strings are equal"
fi
```

