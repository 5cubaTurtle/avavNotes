To be able to call the `pinMode()` and `digitalWrite()` functions in Arduino, you need to include the `Arduino.h` header file. This header file contains the definitions for the standard Arduino functions and constants.

You can include the `Arduino.h` file in your code by adding the following line at the beginning of your sketch:
```c++
#include <Arduino.h>
```
This line tells the Arduino IDE to include the `Arduino.h` file in your sketch. Once you've included this header file, you should be able to call the `pinMode()` and `digitalWrite()` functions in your code.

To set pin D4 on an Arduino board to HIGH using C++, you can use the following code:
```c++
void setup() {
  pinMode(4, OUTPUT); // set pin D4 as an output
}

void loop() {
  digitalWrite(4, HIGH); // set pin D4 to HIGH
}
```
Note that pin D4 is also referred to as pin 4 in the Arduino programming language. The `pinMode()` function is used to configure the pin as an output, and the `digitalWrite()` function is used to set the pin to HIGH or LOW. In this example, we first set pin D4 as an output in the `setup()` function, and then in the `loop()` function, we set it to HIGH using the `digitalWrite()` function.


