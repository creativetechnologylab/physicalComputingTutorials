# What is an LDR?
An LDR or Light Dependent Resistor is a component which restricts how much power can flow through a circuit based on how much or little light hits the sensitive part on the top.

![image](https://github.com/creativetechnologylab/physicalComputingTutorials/assets/64136454/e9545de7-395c-4492-ae6a-52212b8e0544)

To use a Light Dependent Resistor, we have to use it in combination with a fixed value resistor, the combination of these two components acts a little like a kitchen mixer tap, we can vary the temperature (voltage) by adjusting the tap.

![image](https://github.com/creativetechnologylab/physicalComputingTutorials/assets/64136454/0e1e76ea-e936-4ef9-8106-c9948b04c273)

The zig-zag lines indicate resistors, the voltage output we measure with the Arduino comes from this middle point between the two, as the value of the LDR varies it changes the voltage between Ground (0V) and 5V (VCC).


# Wiring
1. (1)leg to 5V (Power)
1. (2)leg split to GND via 10K resistor
1. (2)leg split to A0

![image](https://github.com/creativetechnologylab/physicalComputingTutorials/assets/64136454/cfe06907-17da-49c2-af8d-22d8fd3f6fa8)

# Getting started
The following code uses `analogRead()` to get a integer between 0-1023 representing the voltage, where 0 is 0V and 1023 is 5V.

The code below uses the serial port to output the value every 50ms to the [Serial Monitor](https://learn.adafruit.com/adafruit-arduino-lesson-5-the-serial-monitor/the-serial-monitor).

````
#define ldrPin A0

void setup() {
  Serial.begin( 9600 );
  pinMode( ldrPin, INPUT );
}

void loop() {
  Serial.println( analogRead( ldrPin ) );
  delay( 50 );
}
````
