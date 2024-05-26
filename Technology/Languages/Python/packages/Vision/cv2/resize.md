[guide](https://www.tutorialkart.com/opencv/python/opencv-python-resize-image/)
Enlarge an image by a factor of *6* in both height(`fy`) and width(`fx`) dimensions:
```python
resized_image = cv2.resize(image, None, fx=6, fy=6, interpolation=cv2.INTER_LINEAR)
```

Resize to specific dimensions `new_height` and `new_width`:
```python
new_image = cv2.resize(image, (new_width, new_height))
```