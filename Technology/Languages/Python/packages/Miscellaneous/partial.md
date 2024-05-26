Pass additional arguments to [[createTrackbar|cv2.createTrackbar]] callbacks using the `partila` package:
```python
from functools import partial
cv2.createTrackbar(self._frame_trackbar, self._main_window, self._frame_idx, self._total_frames, partial(foo, param=self))
```
`partial` wraps the function `foo` with the parameter `self` and passes it to the cb registrant - `createTrackber()`.
