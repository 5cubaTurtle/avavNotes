[short guide](https://docs.opencv.org/4.x/dd/d43/tutorial_py_video_display.html)
```PYTHON
recorded_video_file = "recorded_videdo.mp4"  
fourcc = cv2.VideoWriter_fourcc(*'H264') # Specify the FourCC code for H.264 codec  
fps = 10 # Frames per second  
frame_size = (680, 400)  
  
# Create a VideoWriter object to save the video frames  
self.out = cv2.VideoWriter(recorded_video_file, fourcc, fps, frame_size)

#... code to get the video frame ...

out.write(frame) # save the frame to file
```
