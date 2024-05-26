
`range(n,m,i)` produces a list of integers from *n* to *m-1* in increments *i*.

#### Examples
`range(2,11,3)` will yield: [2,5,8]
- Notice that the list does not include the ending argument *11*.

- If no step argument is set, the default *1* will be used:
	`range(0,5)` will yield: [0, 1, 2, 3, 4]

- Range works in the negative direction as well:
	`range(6,-6,-2)` yields: [6, 4, 2, 0, -2, -4]

- Range backwards: `range(6,-6)` yields: []
	Since the step is positive *1* in this case.

- `range(4)` yields: [0,1,2,3]
	If no start argument provided, range starts from 0 by default.
