#python #opencv

##### crate a 20 by 20 pixel image of only one red color.
You can use the `cv2.imwrite()` function in *OpenCV* to create a new image, and the `numpy` library to create a 20x20 *numpy array* filled with a single color (red in this case). Here is an example of how you could create a 20x20 red image:
```python
import cv2
import numpy as np

# Create a 20x20 numpy array filled with red color (BGR format)
red_image = np.zeros((20, 20, 3), dtype=np.uint8)
red_image[:,:] = (0, 0, 255) # color all pixels in red

# Save the image to a file
cv2.imwrite("red_image.jpg", red_image)
```
This will create a new JPG image file in the current working directory with the name "red_image.jpg" containing a 20x20 pixels red image. You can change the format of the image to any other format supported by OpenCV like PNG, BMP and others.

##### draw a vertical or horizontal line
On a 20x20 blue image: `blue_image = np.zeros((20,20, 3), dtype=np.uint8)`
- draw a red horizontal line on the 1st row: `blue[0,:]=(0,0,255)`
- draw a green vertical line on the 3rd column: `blue[:,3]=(0,255,0)`
result image:
![[horizNvert.jpg]]
> assigning a tuple `(0, 0, 255)` to range of values like this on BGR image. To Grayscale assign a single value \[0-255\].
