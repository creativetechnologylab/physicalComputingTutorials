# How to power an Arduino
Here is some resources about powering Arduino or other electronic projects:

### General

How to power an Arduino:
[More information here.](https://www.modmypi.com/blog/how-do-i-power-my-arduino)

How to power a project:  
[More information here.](https://learn.sparkfun.com/tutorials/how-to-power-a-project)

What Adpater:  
[More information here.](http://playground.arduino.cc/Learning/WhatAdapter)


### Portable / Battery powered
For portable projects some info on battery usage.

1.  [How to power your Arduino with battery](http://www.instructables.com/id/Powering-Arduino-with-a-Battery/ )
1. [How to choose your battery](https://learn.adafruit.com/all-about-batteries/overview)
1. [Indepth Arduino powering guide](https://www.open-electronics.org/the-power-of-arduino-this-unknown/)
1. [Why 9V batteries are bad](https://cybergibbons.com/uncategorized/arduino-misconceptions-6-a-9v-battery-is-a-good-power-source/)

### Power Banks
Not all power banks are good for microcontrollers as they mostly have a safety feature which is auto-off when consumption is low. Microcontrollers often have a low-current consumption and the power bank will auto-off every a few minutes. However, there are some power banks that can support low-current charging mode/ always-on mode. These will be suitable for powering a microcontroller, e.g. *Sandberg Powerbank 20000 PD65W 2xQC3.0*. (We only tested this one, but other brands and models can do the same.)


### Motors
There are many different types of motors available. Before deciding how to power your motor, you must know what **voltage** the motor is going to use and how much **current** your motor will need.

1. Guide for powering motors with Raspberry Pi: [here](https://learn.adafruit.com/adafruit-dc-and-stepper-motor-hat-for-raspberry-pi/powering-motors). 
1. Guide for Adafruit Motor Shield with Arduino: [here](https://learn.adafruit.com/adafruit-motor-shield-v2-for-arduino/powering-motors).
