# What is the HC-SR04?
The HC-SR04 is a ultrasonic distance sensor, it uses ultrasound to send out a ping and measure how long the sound takes to come back, exactly like bats use to fly in the dark.

The sensor works between 2-400cm however if the ping sound is reflected away from the sensor by an a divergent (not parallel) surface, or absorbed by a soft surface like fabric there may no measurement.

There are other types of distance sensors that are more accurate for projects where needed, this is a cheap < £5 sensor, while more accurate ones are over £100.

# Wiring
Wiring up the sensor is simple:

1. Power (VCC to 5V)
1. Ground (GND to GND)
1. Echo to digital pin 12
1. Trigger to digital pin 13

![image](https://github.com/creativetechnologylab/physicalComputingTutorials/assets/64136454/f46a6eed-1c1c-4b92-b1be-99f88633f549)



# Getting started

This example turns on an LED when the distance measured is less than 30cm and back off when the distance goes over 30cm.

````
#include <HCSR04.h>

// Initialize sensor that uses digital pins 13 and 12.
UltraSonicDistanceSensor distanceSensor(13, 12);  

void setup () {
    Serial.begin(9600);  //initialize serial connection so that we could print values from sensor.
    pinMode(13, OUTPUT);
}

void loop () {

    float distance = distanceSensor.measureDistanceCm();
    Serial.println(distance);

    if (distance < 30 ){
       digitalWrite(13, HIGH);
       delay(100);
      }else{
         digitalWrite(13, LOW);
         delay(100);
        }
}
````

To use this code you will need the [HCSR04 Library](https://www.arduinolibraries.info/libraries/hcsr04) by Martin Sosic.

We have a tutorial on [how to install a library](https://lab.arts.ac.uk/books/physical-computing/page/how-to-install-libraries) here.
