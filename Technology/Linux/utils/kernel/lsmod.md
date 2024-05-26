#linux 
Show the status of modules in the Linux Kernel

see if  ov9281 module is installed: `lsmod |grep ov9281`

	ov9281                 20480  1
	v4l2_fwnode            32768  2 ov9281,bcm2835_unicam
	videodev              315392  9 bcm2835_codec,v4l2_fwnode,ov9281,videobuf2_v4l2,bcm2835_unicam,bcm2835_v4l2,videobuf2_common,v4l2_mem2mem,bcm2835_isp
	mc                     73728  8 videodev,bcm2835_codec,ov9281,videobuf2_v4l2,bcm2835_unicam,videobuf2_common,v4l2_mem2mem,bcm2835_isp