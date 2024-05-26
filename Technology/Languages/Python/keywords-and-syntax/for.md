#python #flow-control
**for** \<name\> **in** \<list\>:
    \<block\>

Example:
```python
def print_all_elements (p):   #prints out p
    for e in p:      # e is a name assigned to each succeeding element
	    print e      # of p at each iteration
```

If the list `p` contains lists in itself , we could refer to these elements directly in the following manner:

```python
p=[['sugar',5],['salt',7]['pepper',1]]    # a list of ingredients and grams

for ingredient, weight in p:
    print(weight)
    print(ingredient)
```
This prints the second element of each list \(weight\) followed by the first element of each list \(ingredient\). 
>Notice that the statement has to have the exact number of values contained in each list. This in turn means that each sub-list has to have the same number of values.
