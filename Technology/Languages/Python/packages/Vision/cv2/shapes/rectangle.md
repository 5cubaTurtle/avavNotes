draw rectangle on an image:
```python
cv2.rectangle(img, up_left_corner, down_right_corner, shade, thickness)
```
`img` is the image matrix, `up_left/down_right_corner` are tuple coordinates of opposite corners of the rectangle. The `shade` is [[int]] in range of 0-255 on a gray-scale image. `thickness` in pixels.
