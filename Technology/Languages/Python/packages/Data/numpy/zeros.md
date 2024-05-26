`zeros(shape, dtype=float, order='C')`

Return a new array of given shape and type, filled with zeros.  
  
Parameters  
-------  
shape : int or tuple of ints  
Shape of the new array, e.g., ``(2, 3)`` or ``2``.  
dtype : data-type, optional  
The desired data-type for the array, e.g., `numpy.int8`. Default is  
`numpy.float64`.  
order : {'C', 'F'}, optional, default: 'C'  
Whether to store multi-dimensional data in row-major  
(C-style) or column-major (Fortran-style) order in  
memory.  
  
Returns  
-------  
out : [[ndarray]]  
Array of zeros with the given shape, dtype, and order.