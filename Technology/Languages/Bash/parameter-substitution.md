#bash 

from [tldp website](https://tldp.org/LDP/abs/html/parameter-substitution.html):
`${var#Pattern}` Remove from `$var` the _shortest_ part of `$Pattern` that matches the _front end_ of `$var`.

`${var##Pattern}` Remove from `$var` the _longest_ part of `$Pattern` that matches the *front end* of `$var`.

`${var%Pattern}` Remove from `$var` the _shortest_ part of `$Pattern` that matches the _back end_ of `$var`.

`${var%%Pattern}` Remove from `$var` the _longest_ part of `$Pattern` that matches the _back end_ of `$var`.

more succint page in [devhints.io/bash](https://devhints.io/bash)

get first 3 characters of a string:   `${string:0:3}`
get last 3 characters of a string:   `${string: -3}`

assign `var` to `a` if `var` is defined, else assign the output of `pwd` command:
	`a=${vis:-$(pwd)}; echo $a`
