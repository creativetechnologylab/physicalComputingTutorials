# How to construct a robotic arm?
A simple robotic arm is basically like a human arm which consists of the upper arm, lower arm and hand (gripper). There are a lot of online resources for laser-cut files that you can use. After you have found one or designed one, you can go to the 3D Workshop to laser cut the hardware. In this tutorial, we will focus on how to control the servo motor (the joint of your robotic arm) with two potentiometers.

![image](https://github.com/creativetechnologylab/physicalComputingTutorials/assets/64136454/953e767a-2640-428c-9df7-05b8778f6421)

You can use more or less servo motors in your design based on how many joints you need. In this tutorial, we will use two servo motors, one for the rotation at the base and one for the angle of the upper arm.

# Wiring

1. **Servo:** Power to 5V
1. **Servo:** Ground to GND
1. **Servo:** Signal to 6/10
1. **Potentiometer:** Right pin to 5V
1. **Potentiometer:** Left pin to GND
1. **Potentiometer:** Middle pin to A0/A1

![image](https://github.com/creativetechnologylab/physicalComputingTutorials/assets/64136454/f83f8d34-bbbd-4728-871a-eb47143d73cf)

# Getting started
This code is getting the servo motors to rotate based on the potentiometers' values.

```c++
#include <Servo.h>

#define potRotation      A0 
#define potAngle      A1 
#define servoRotation  10  
#define servoAngle  6 

// create servo object to control a servo 
Servo rotateServo;  
Servo angleServo; 

void setup() {
  Serial.begin(9600) ;
  rotateServo.attach(servoRotation);
  angleServo.attach(servoAngle);
}

void loop() {
  // read analog potentiometer values
  int rotation = analogRead(potRotation);
  int angle = analogRead(potAngle);

  int rotationMapped = map(rotation, 0, 1023, 0, 180); // scale it to the servo's angle (0 to 180)
  int angleMapped = map(angle, 0, 1023, 0, 180); // scale it to the servo's angle (0 to 180)

  rotateServo.write(rotationMapped); // rotate servo motor 1
  angleServo.write(angleMapped); // rotate servo motor 2

  // print data to Serial Monitor on Arduino IDE
  Serial.print("potRotation: ");
  Serial.print(rotation);
  Serial.print(", potAngle:");
  Serial.print(angle);
  Serial.print(" => Servo Motor Rotation: ");
  Serial.print(rotationMapped);
  Serial.print("°, Angle:");
  Serial.print(angleMapped);
  Serial.println("°");
}
}
```
