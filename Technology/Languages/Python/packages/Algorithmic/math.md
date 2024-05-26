#python

### Trigonometry
```python
import math

# convert an angle from degrees to radians
angle_degrees = 45
angle_radians = math.radians(angle_degrees)

# calculate the sine, cosine, and tangent of an angle
sine = math.sin(angle_radians)
cosine = math.cos(angle_radians)
tangent = math.tan(angle_radians)

# calculate the arc sine, arc cosine, and arc tangent of a value
value = 0.5
arc_sine = math.asin(value)
arc_cosine = math.acos(value)
arc_tangent = math.atan(value)

# calculate the hypotenuse of a right triangle
opposite = 3
adjacent = 4
hypotenuse = math.hypot(opposite, adjacent)

# convert a rectangular coordinate to polar coordinates
x = 3
y = 4
distance = math.hypot(x, y)
angle = math.atan2(y, x) # returns an angle in radians

# convert a polar coordinate to rectangular coordinates
angle = math.pi/4 # 45 degrees
distance = 5
x = distance * math.cos(angle)
y = distance * math.sin(angle)
```
The `math` module also provides functions for working with hyperbolic trigonometry, complex numbers, and more.

### Modulo math.fmod()
from [askpython](https://www.askpython.com/python/python-modulo-operator-math-fmod):
The behavior of % operator with negative numbers is different from the platform C library. If you want the modulo operation to behave like C programming, you should use math module fmod() function. This is the recommended function for getting modulo with floating point numbers.
```python
import math
math.fmod(-5, 3)
>>> -2.0
math.fmod(5, 3)
>>> 2.0
math.fmod(-10, 3)
>>> -1.0
```
-   fmod(-5, 3) = fmod(-2 -1*3, 3) = -2.0
-   fmod(5, -3) = fmod(2 -1*-3, -3) = 2.0
-   fmod(-10, 3) = fmod(-1 -3*3, 3) = -1.0

#### Warning about using modulo on floats
```python
9.6 % 3.2
>>> 3.1999999999999993
```
The output should be 0 because 3.2*3 is 9.6. But, the float fraction values are not exactly represented and the approximation is causing this error.
