[doc](https://docs.opencv.org/4.9.0/d4/da8/group__imgcodecs.html#gabbc7ef1aa2edfaa87772f1202d67e0ce)
The `imread` and `imwrite` functions don't throw exceptions on errors, but fail silently. `imwrite` returns `False`
Save image to a file
```python
if not cv2.imwrite('output.jpg', image):
	raise Exception("Could not write image")
```
