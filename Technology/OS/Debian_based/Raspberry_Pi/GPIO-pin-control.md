[doc](https://www.raspberrypi.com/documentation/computers/os.html#gpio-and-the-40-pin-header)
1. Stop the *br-always-on* service. It turns off the leds if the robot is not launched.
2. write *1* to pin *gpio18*:
```sh
if [ ! -e /sys/class/gpio/gpio18 ]; then
    echo "18" > /sys/class/gpio/export
fi
echo "out" > /sys/class/gpio/gpio18/direction
echo "1" > /sys/class/gpio/gpio18/value
```
The first 4 lines setup the pin 18:
`echo "18" > ..` exports the pin 18 and `echo "out > .."` sets pin 18 to *output* mode.
The last line `echo "1" > ..` actually sets the pin to value *1*.
