#numpy 
#### tolist()
The `tolist()` method of a NumPy `ndarray` object is used to return a copy of the array data as a standard Python list:
```python
import numpy as np

arr = np.array([[1, 2, 3], [4, 5, 6]])
lst = arr.tolist()

print(lst)
# Output: [[1, 2, 3], [4, 5, 6]]
```
we create a NumPy array `arr` that contains two rows and three columns of data. We then call the `tolist()` method to convert `arr` to a Python list. The resulting `lst` list has the same shape and elements as `arr`, but is a standard Python list.

Note that `tolist()` creates a new copy of the array data, so any changes made to the list will not affect the original NumPy array object. Additionally, if the original NumPy array has a complex data type (e.g. complex numbers), the resulting list will contain tuples instead of simple values.

#### astype()
To change the [[dtype]] attribute of ndarray us `astype()`:
```python
thresh_image = thresh_image.astype('uint8')
```

### math operators (+,-,\* or /)
Applying a math operation with a number on a ndarray will perform it on all it's elements. For example, subtracting a number from a ndarray will subtract the number from all elements in the array.
```python
<<<: type(image)
>>>: numpy.ndarray
<<<: image
>>>: 
array([[239, 196, 167, ..., 115,  35, 227],
       [  2, 142, 178, ...,  89,   6,  41],
       [251, 235, 219, ..., 141,  71, 240],
       ...,
       [  7,  10,  16, ...,  48,  61, 197],
       [  6, 138, 234, ...,   7, 116, 222],
       [189,  17, 232, ..., 246, 207,  70]], dtype=uint8)

<<<: minus = image - 3

<<<: minus
>>>: 
array([[236, 193, 164, ..., 112,  32, 224],
       [255, 139, 175, ...,  86,   3,  38],
       [248, 232, 216, ..., 138,  68, 237],
       ...,
       [  4,   7,  13, ...,  45,  58, 194],
       [  3, 135, 231, ...,   4, 113, 219],
       [186,  14, 229, ..., 243, 204,  67]], dtype=uint8)
```

### iteration over ndarray
To iterate over a NumPy ndarray (n-dimensional array), you can use various techniques such as loops or specific NumPy functions designed for iteration. Here are some common methods to achieve this:

1. Using a `for` loop:
   You can iterate over each element in the ndarray using a simple `for` loop. For multi-dimensional arrays, you can use nested loops to traverse each dimension. Here's an example:
```python
arr = np.array([[1, 2], [3, 4], [5, 6]])
# Using nested loops for a 2D array
for row in arr:
    for element in row:
        print(element)
```

2. Using `np.nditer`:
   The `np.nditer` function allows you to iterate over elements in the array, regardless of its shape or dimension. It provides more flexibility and efficiency than standard Python loops:
```python
arr = np.array([[1, 2], [3, 4], [5, 6]])
# Using np.nditer for a 2D array
for element in np.nditer(arr):
    print(element)
```

3. Using `np.ndenumerate` (with index):
   If you also need the indices while iterating, you can use `np.ndenumerate`:
```python
arr = np.array([[1, 2], [3, 4], [5, 6]])
# Using np.ndenumerate for a 2D array
for index, element in np.ndenumerate(arr):
    print(f"Index {index}: {element}")
```

4. Using Boolean masking:
   NumPy also supports boolean indexing and masking, which can be useful for filtering elements based on certain conditions:
```python
arr = np.array([1, 2, 3, 4, 5])
# Using boolean masking to iterate over specific elements
for element in arr[arr % 2 == 0]:
    print(element)
```

5. Vectorized operations (preferred):
   In many cases, you can perform element-wise operations without explicit iteration. NumPy is optimized for vectorized operations, which are usually more efficient and concise:
```python
arr = np.array([1, 2, 3, 4, 5])
# Example of vectorized operations without explicit iteration
squared = arr**2
print(squared)
```
Using vectorized operations is often preferred because it takes advantage of NumPy's efficient implementation and can lead to faster code execution.
