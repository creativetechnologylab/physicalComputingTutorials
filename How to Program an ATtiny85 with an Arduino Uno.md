# What is an ATtiny85?
ATtiny85 is a 8-bit AVR microcontroller based on AVR enhanced RISC architecture. It has an 8-pin interface (PDIP) and comes in the category of low-power microcontrollers. This microcontroller is designed and manufactured by Microchip.
[Know More](https://www.microchip.com/en-us/product/ATtiny85)


![image](https://github.com/creativetechnologylab/physicalComputingTutorials/assets/64136454/7c3a375e-f5b3-4cdc-94ef-14510a76a4ad)


# Set the Arduino Uno Into ISP Mode
So that the Arduino can act as a device to upload code to ATtiny85.
`File - Examples - Arduino ISP - ArduinoISP`

Add  this line `#define USE_OLD_STYLE_WIRING` to the code before `setup()`


**UPLOAD!**

# Wiring
The pins are not labelled so you will have to refer to the pinout.
![image](https://github.com/creativetechnologylab/physicalComputingTutorials/assets/64136454/9e5f3df8-0a32-4e96-ad9a-2f82ec0684a2)

Arduino --> ATtiny85

1. 5V    -->        Vcc (8)              
1. GND  -->         GND (4)               
1. Pin 13  -->      Pin 2 (7)
1. Pin 12    -->    Pin 1 (6)
1. Pin 11    -->    Pin 0 (5)
1. Pin 10    -->    Reset (1)

<p class="callout warning"> <b>Only when you are uploading code to ATtiny85</b><br / > Put a 10uF capacitor between GND and RESET on Arduino <br / ></p>

# Adding Attiny85 to Boards Manager 
We have to make ATtiny compatible with Arduino IDE first, so that we can choose ATting85 from `Tools -> Board`
</br>Go to `Arduino Preference`

</br>Copy the below code and paste it into `Additional Boards Manager URLs`, if you already have a board manager URL just add a comma before pasting. Click OK and restart Arduino IDE.

`https://raw.githubusercontent.com/damellis/attiny/ide-1.6.x-boards-manager/package_damellis_attiny_index.json`

![image](https://github.com/creativetechnologylab/physicalComputingTutorials/assets/64136454/83dbbda4-1e2d-4bf4-a067-7e3d44a35436)


Go to `Tools - Board - Boards Manager`, search for ATtiny, then install!
![image](https://github.com/creativetechnologylab/physicalComputingTutorials/assets/64136454/bc599915-a907-4f3e-86e0-ba361b66dc3d)


# Get Started
Before uploading the code, we have to change some settings.

1. Tools -> Board scroll to the bottom select ATtiny25/45/85
1. Tools -> Processor--> 8 MHz (internal)
1. Tools-->Programmer-->Arduino as ISP
1. Check that all wiring, capacitor, and board selections are correct.

![image](https://github.com/creativetechnologylab/physicalComputingTutorials/assets/64136454/9128f3a8-cc87-400c-8d68-5d3f6ec0ac3c)

**Open up a basic code and upload as usual!**
</br>If it doesn't work, try `Tools - Burn Bootloader`
