# What is a Hall Effect Sensor?
The hall effect sensor is a type of magnetic sensor which can be used for detecting the strength and direction of a magnetic field produced from a permanent magnet or an electromagnet with its output varying in proportion to the strength of the magnetic field being detected.

![image](https://github.com/creativetechnologylab/physicalComputingTutorials/assets/64136454/42e88103-e725-4fdd-9701-10b4a1e43575)

# Wiring
1. left to 5V (Power)
1. middle to GND 
1. right to PIN2 via 10K resistor
![image](https://github.com/creativetechnologylab/physicalComputingTutorials/assets/64136454/5d971a94-7ff9-4a62-bbf3-f09a5c052094)


# Getting started
The following code uses `digitalRead()` to get a integer (1/0) representing the detection of magnet.


````
const int hallSensorPin = 2;  // Hall Effect sensor connected to digital pin 2
int hallSensorState;          // Variable to store the state of the sensor

void setup() {
  Serial.begin(9600);                // Start serial communication at 9600 baud
  pinMode(hallSensorPin, INPUT);     // Set the Hall Effect sensor pin as an INPUT
}

void loop() {
  hallSensorState = digitalRead(hallSensorPin); // Read the state of the sensor
  Serial.println(hallSensorState); 

  delay(100); 
}
````
