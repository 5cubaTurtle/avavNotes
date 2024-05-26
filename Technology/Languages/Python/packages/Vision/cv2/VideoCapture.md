#opencv #python 
Class for video capturing from video files, image sequences or cameras.
[doc version 4.2.0](https://docs.opencv.org/4.2.0/d8/dfe/classcv_1_1VideoCapture.html)

example:
```python
cap = cv2.VideoCapture(0, cv2.CAP_V4L2)
ret, frame = cap.read()
```
The `frame` variable should contain a single video frame captured from the camera. The format of the frame data depends on the specific camera being used, but typically it will be a NumPy array with dimensions (height, width, channels), where `height` and `width` are the dimensions of the frame in pixels, and `channels` is the number of color channels in the image (e.g. 3 for RGB or 1 for grayscale). Most often the type of `frame` is [[ndarray|numpy.ndarray]].

The exact data type of the `frame` array depends on the camera and the video capture settings, but it is typically an unsigned 8-bit integer (i.e. `dtype=np.uint8`) or a floating-point number (i.e. `dtype=np.float32`). The range of pixel values in the `frame` array will also depend on the specific camera and settings.

To work with the `frame` data, you can use the many image processing functions provided by the OpenCV library, which support a wide range of image formats and operations. For example, you can use functions like `cv2.cvtColor` to convert the color space of the image, `cv2.imshow` to display the image on the screen, and `cv2.imwrite` to save the image to disk in a specific format.

### reading images
Format of the image:
```python
import cv2
cap = cv2.VideoCapture(0)
ret, frame = cap.read()
print(frame.shape)
print(frame.dtype)
```
The python-type of the `frame`  here is `np.ndarray`.
Shape of the captured image in the form `(height, width, channels)`, where `height` and `width` are the dimensions of the image in pixels, and `channels` is the number of color channels in the image (e.g. 3 for RGB or 1 for grayscale).
Data type of the image array, which will typically be uint8 for 8-bit unsigned integer arrays, or float32 for floating-point arrays.
data type of the `frame` array depends on the camera and the video capture settings, but it is typically an unsigned 8-bit integer (i.e. `dtype=np.uint8`) or a floating-point number (i.e. `dtype=np.float32`). The range of pixel values in the `frame` array will also depend on the specific camera and settings.

To work with the `frame` data, you can use the many image processing functions provided by the OpenCV library, which support a wide range of image formats and operations. For example, you can use functions like [[cvtColor|cv2.cvtColor]] to convert the color space of the image, [[imshow|cv2.imshow]] to display the image on the screen, and [[imwrite|cv2.imwrite]] to save the image to disk in a specific format.

### set()
Sets a property in the [VideoCapture](https://docs.opencv.org/3.4/d8/dfe/classcv_1_1VideoCapture.html "Class for video capturing from video files, image sequences or cameras."). [doc](https://docs.opencv.org/3.4/d8/dfe/classcv_1_1VideoCapture.html#a8c6d8c2d37505b5ca61ffd4bb54e9a7c)
Setting resolution of the frames as they are read from the camera.
```python
cap.set(cv2.CAP_PROP_FRAME_WIDTH, 128)
cap.set(cv2.CAP_PROP_FRAME_HEIGHT, 96)
```
>[!Note] 
>This is not setting the resolution of the resultant frame after `cap.read()`, this is setting the resolution of the camera.

### get()
Returns the specified [VideoCapture](https://docs.opencv.org/3.4/d8/dfe/classcv_1_1VideoCapture.html "Class for video capturing from video files, image sequences or cameras.") property. [doc](https://docs.opencv.org/3.4/d8/dfe/classcv_1_1VideoCapture.html#aa6480e6972ef4c00d74814ec841a2939)

#### video capture API backend
`cv2.CAP_V4L2` is a video capture API backend that allows the library to interface with video capture devices that support the Video4Linux2 (V4L2) API. V4L2 is a standard Linux kernel API for supporting video devices such as webcams, digital cameras, and video capture cards.

When creating a new `cv2.VideoCapture` object, the second argument can be used to specify the video capture API backend to use. By passing `cv2.CAP_V4L2` as the second argument, the OpenCV library will use the V4L2 backend to interface with the video capture device.

Note that not all video capture devices support the V4L2 API, and in some cases a different backend may be required. Other possible values for the second argument of `cv2.VideoCapture` include `cv2.CAP_DSHOW` for DirectShow on Windows, `cv2.CAP_FFMPEG` for FFmpeg, and `cv2.CAP_GSTREAMER` for GStreamer on Linux.