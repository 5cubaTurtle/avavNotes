#opencv 
##### [getBuildInformation()](https://docs.opencv.org/4.x/db/de0/group__core__utils.html#ga0ae377100bc03ce22322926bba7fdbb5)
Returns full configuration time cmake output.
[Guide](https://note.nkmk.me/en/python-opencv-getbuildinformation/): Some of the features of OpenCV need to be enabled at build.
You can check the build information of OpenCV with `getBuildInformation()`:
```sh
python -c 'import cv2; print(cv2.getBuildInformation())' 
python -c 'import cv2; print(cv2.__version__)' # show version
```
