Applying a math operation with a number on a [[ndarray]] will perform it on all it's elements. For example, subtracting a number from a [[ndarray]] will subtract the number from all elements in the array.
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