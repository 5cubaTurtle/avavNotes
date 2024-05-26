Add and remove modules from the Linux Kernel

remove a module: `modeprobe -r <module>`
To install a driver (*ov9281.ko* in this case):
```sh
sudo cp ov9281.ko 
sudo depmod
sudo modprobe ov9281
sudo reboot
```

