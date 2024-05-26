create window

A [doc](https://docs.opencv.org/4.x/d7/dfc/group__highgui.html#ga5afdf8410934fd099df85c75b2e0888b), and a [better one](https://www.opencv.org.cn/opencvdoc/2.3.2/html/modules/highgui/doc/user_interface.html#namedwindow "Permalink to this headline").

create a window named *Test* and move it to coordinate (40, 30):
```python
img = cv2.imread("test.png")
winname = "Test"
cv2.namedWindow(winname, cv2.WINDOW_NORMAL) # user can resize window_normal
cv2.moveWindow(winname, 40, 30)  # Move it to (40, 30)
cv2.imshow(winname, img)
cv2.waitKey()
cv2.destroyAllWindows()
```
after the `winname`, `flags` could be provided. Default flags are `flags == WINDOW_AUTOSIZE | WINDOW_KEEPRATIO | WINDOW_GUI_EXPANDED`.
-   **WINDOW_NORMAL** or **WINDOW_AUTOSIZE**: `WINDOW_NORMAL` enables you to resize the window, whereas `WINDOW_AUTOSIZE` adjusts automatically the window size to fit the displayed image (see imshow ), and you cannot change the window size manually.
-   **WINDOW_FREERATIO** or **WINDOW_KEEPRATIO**: `WINDOW_FREERATIO` adjusts the image with no respect to its ratio, whereas `WINDOW_KEEPRATIO` keeps the image ratio.
-   **WINDOW_GUI_NORMAL** or **WINDOW_GUI_EXPANDED**: `WINDOW_GUI_NORMAL` is the old way to draw the window without statusbar and toolbar, whereas `WINDOW_GUI_EXPANDED` is a new enhanced GUI.

also see 
### [setWindowProperty](https://docs.opencv.org/4.x/d7/dfc/group__highgui.html#ga66e4a6db4d4e06148bcdfe0d70a5df27)
set window to full screen:
```python
cv2.setWindowProperty(self._processed_window, cv2.WND_PROP_FULLSCREEN, cv2.WINDOW_FULLSCREEN)
```
