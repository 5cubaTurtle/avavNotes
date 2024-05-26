Drawing green vertical line:
```python
# Get the image dimensions
height, width, _ = image.shape

# Set the coordinates for the vertical line
x = 90  # x-coordinate of the line
y1 = 0  # Start y-coordinate of the line (top of the image)
y2 = height - 1  # End y-coordinate of the line (bottom of the image)

# Set the line color (in BGR format)
color = (0, 255, 0)  # Green color

# Draw the vertical line on the image
cv2.line(image, (x, y1), (x, y2), color, thickness=1)
```
or use [[color-row-column|numpy]] method `image[:,x_location] = (0, 255, 0)` if you want a vertical or horizontal line.

