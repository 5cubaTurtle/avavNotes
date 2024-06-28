![dictVsListVsString.png](dictVsListVsString.png)

calling for a value in a dictionary we use the key associated with it:
`dic={'a': 1, 'b':2, 'c': 3}`
`dic['b']`   yields *2*

- calling an absent key produces a 'key' error.
- adding or changing an element:
`dic['d']=4` mutates the dic to \{'a': 1, 'b':2, 'c': 3, 'd':4\}
or
`dic['c']=9` mutates the dic to \{'a': 1, 'b':2, 'c': 9\}

- a dictionary could have several sets of keys and values i.e. a dictionary within a dictionary:
`dic={'animals':{'cat':'black', 'dog': 'brown', 'rabbit': 'white'}}`