#python 

create list of 5 `None`s:
```python
>>> l=[None]*5
>>> l
[None, None, None, None, None]
```
#### Range of indexes
extract from the list every *2nd* element from the *3rd* element to the *9th*: `mylist[3:9:2]` or get the last 3 elements in reverse order: `mylist[-1:-4:-1]`
from [w3schools](https://www.w3schools.com/python/python_lists_methods.asp)

#### functions
[append()](https://www.w3schools.com/python/ref_list_append.asp) - Adds an element at the end of the list
`list.append(element)` adds `element` to the end of the `list`

[clear()](https://www.w3schools.com/python/ref_list_clear.asp) - Removes all the elements from the list
[copy()](https://www.w3schools.com/python/ref_list_copy.asp) - Returns a shallow copy of the list
[count()](https://www.w3schools.com/python/ref_list_count.asp) - Returns the number of elements with the specified value
[extend()](https://www.w3schools.com/python/ref_list_extend.asp) - Add the elements of a list (or any iterable), to the end of the current list

[index](https://www.w3schools.com/python/ref_list_index.asp) - Returns the index of the first element with the specified value
`list.index(value)` this gives the `index` of the 1st `value` in the `list`

[insert()](https://www.w3schools.com/python/ref_list_insert.asp) - Adds an element at the specified position

[pop()](https://www.w3schools.com/python/ref_list_pop.asp) - Removes the element at the specified position
`list.pop()` mutates the `list` by removing and returning its last element

[remove()](https://www.w3schools.com/python/ref_list_remove.asp) - Removes the item with the specified value
[reverse()](https://www.w3schools.com/python/ref_list_reverse.asp) - Reverses the order of the list
[sort()](https://www.w3schools.com/python/ref_list_sort.asp) - Sorts the list

##### list.sort() vs sorted(list)
The `sorted(my_list)` and `my_list.sort()` are both used to sort a list in Python, but they have some differences in their behavior and return values:
1. Return Value:
    - `sorted(my_list)` returns a new sorted list and leaves the original list unchanged.
    - `my_list.sort()` sorts the list in-place and returns `None`. The original list is modified.
2. Mutability:
    - `sorted(my_list)` does not modify the original list and returns a new sorted list.
    - `my_list.sort()` modifies the original list in-place and does not create a new list.

### Typed list
To create a typed list in Python, you can make use of type hints in combination with the `List` generic class from the `typing` module:
```python
from typing import List

# Define the type of elements in the list
Element = int

# Create a typed list
my_list: List[Element] = [1, 2, 3, 4, 5]

# Access and modify elements
print(my_list[0])        # Output: 1
my_list.append(6)
print(my_list)           # Output: [1, 2, 3, 4, 5, 6]
```
We then define a variable `my_list` with type hinting syntax, indicating that it is a list of `Element` type elements (`List[Element]`). In this case, it is a list of integers.
Using type hints helps improve code readability and provides static type checking benefits. However, since Python is a dynamically-typed language, the type hints are not enforced at runtime. It's up to the developer to ensure that the list contains elements of the specified type.