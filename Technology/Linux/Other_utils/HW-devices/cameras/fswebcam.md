fswebcam  is a small and simple webcam app for \*nix. It can capture images from a number of different sources and perform simple manipulation on the captured image. The image can be saved as one or more PNG or JPEG files.
[guide in rpi](https://www.raspberrypi.com/documentation/computers/os.html#basic-usage)

Capture from */dev/video2*: `fswebcam -d /dev/video2 c2.jpg`.
	- Default device is */dev/video0*.
	- The output image will be saved to `c2.jpeg` 	file.
	