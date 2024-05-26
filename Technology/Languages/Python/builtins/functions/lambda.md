passing a callback to [[createTrackbar|cv.createTrackbar]]:
```python
cv2.createTrackbar(self._frame_trackbar, self._main_window, self._frame_idx, self._total_frames, lambda frame_num: self.display_frame_and_wait4key(frame_num))
```
the `createTrackbar` accepts a callback which receives one parameter thus the signature of the lambda is `lambda frame_num:`.
