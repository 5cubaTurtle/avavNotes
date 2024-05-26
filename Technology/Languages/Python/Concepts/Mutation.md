The difference between the `.append()` and `+` operations:
`.append` actually mutates the list it operates upon while the `+` statement simple creates a third list from the two previous lists: \[a,b\]\+\[c\]=\[a,b,c\] which is a new list.
where is: \[a,b\].append\(c\)=\[a,b,c\] is in fact the same old \[a,b\] list mutated to \[a,b,c\].
This difference could be seen when we define a procedure:
```python
def proc(mylist):
    mylist = mylist + [6]

def proc2(mylist):
    mylist.append(6)
```

The first procedure `proc` would not produce any change in its object list, while the `proc2` would in fact add the element 6 to the object list.

the `+=` operation is equivalent to `.append()` and not `+` (i.e. it mutates), however `+=` could be applied to int as well (not only lists).

furthermore, `.append()` can only take one element where's `+` or `+=` can take as many arguments as we please:

if we have a list `p=[1,2,3]`, we might have:
`p.append(5)` (=`[1,2,3,5]`) or `p.append([5,6,7])` (=`[1,2,3,[5,6,7]]`) but not `p.append(5,6,7)` (error), therefore we can append a single integer to a list or a list of integers, but not several integers.

with `+` or `+=` on the other hand we could:
`p+[5,6,7]` (=`[1,2,3,5,6,7]`) or `p+[[5,6,7]]` (=`[1,2,3,[5,6,7]]`).

same applies to `+=` operand.
