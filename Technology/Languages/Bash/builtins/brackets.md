#bash 
[Brackets vs parantheseis](https://unix.stackexchange.com/a/306115)
`[[` vs. `[`
`[[` is a bash built-in, and cannot be used in a `#!/bin/sh` script. You'll want to read the [Conditional Commands](http://www.gnu.org/software/bash/manual/bashref.html#Conditional-Constructs) section of the bash manual to learn the capabilities of `[[`. The major **benefits**:
-   `==` and `!=` perform pattern matching, so the right-hand side can be a glob pattern
-   `=~` performs regular expression matching. Captured groups are stored in the `BASH_REMATCH` array.
-   boolean operators `&&` and `||`
-   parenthèses for grouping of expressions.
-   no word splitting, so it's not strictly necessary to quote your variables.
**Drawback**: bash-specific syntax.
