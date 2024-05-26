creates slider
[doc](https://www.opencv.org.cn/opencvdoc/2.3.2/html/modules/highgui/doc/user_interface.html#createtrackbar)

```python
cv2.createTrackbar("frame", self._main_window, self._frame_idx, self._total_frames, lambda frame_num: self.display_frame(frame_num))
```