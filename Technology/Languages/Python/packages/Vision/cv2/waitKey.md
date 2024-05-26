[doc](https://docs.opencv.org/4.x/d7/dfc/group__highgui.html#ga5628525ad33f52eab17feebcfba38bd7)
`cv2.waitKey()` function is used to wait for a keyboard event.
```python
# Display the image
cv2.imshow('Image', img)
# Wait for a keyboard event, and store the key code in a variable
key = cv2.waitKey(0)
# Check if the 'ESC' key was pressed
if key == 27:
    cv2.destroyAllWindows()
```
`cv2.imshow('Image', img)` displays the image on the screen. Then, `cv2.waitKey(0)` waits for a keyboard event, and returns the key code of the pressed key. The argument `0` passed to `cv2.waitKey()` means that the function waits indefinitely for a key event, until the user presses a key. If you pass a positive integer as an argument, it means the function waits for that many *milliseconds* for a key event, and returns -1 if no key is pressed within that time.