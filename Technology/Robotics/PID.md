[ctrl+alt+ftc guide](https://www.ctrlaltftc.com/the-pid-controller)
PID Controller consists of three main parts. The Proportional (P), the Integral (I), and the Derivative (D).
![[PID_schematics.png]]
Pseudo code of PID:
```java
/*
* Proportional Integral Derivative Controller 
*/

Kp = someValue;
Ki = someValue;
Kd = someValue;
reference = someValue;
integralSum = 0;
lastError = 0; 

// Elapsed timer class from SDK, please use it, it's epic
ElapsedTime timer = new ElapsedTime();

while (setPointIsNotReached) {
    // obtain the encoder position 
    encoderPosition = armMotor.getPosition();
    // calculate the error 
    error = reference - encoderPosition;
    
    // rate of change of the error 
    derivative = (error - lastError) / timer.seconds();
    
    // sum of all error over time
    integralSum = integralSum + (error * timer.seconds());

    out = (Kp * error) + (Ki * integralSum) + (Kd * derivative);        
    armMotor.setPower(out);
    lastError = error; 
    
    // reset the timer for next time 
    timer.reset();
}
```
