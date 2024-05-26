#cv2
[doc](https://docs.opencv.org/4.9.0/d4/da8/group__imgcodecs.html#ga288b8b3da0892bd651fce07b3bbd3a56)
load an image: `image = cv2.imread('path/to/image.png')`
load image as grayscale:
```python
image = cv2.imread('path/to/image.png', cv2.IMREAD_GRAYSCALE)
```
If the image cannot be read (because of missing file, improper permissions, unsupported or invalid format), the function returns an empty matrix.