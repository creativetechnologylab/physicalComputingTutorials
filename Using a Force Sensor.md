# What is a Force Sensor?
The Force Sensor senses the resistance value depending on how much it has pressed. It can sense even the slightest touch, therefore you can use it as a touch sensor as well. The difference between this and [Capacitive Sensor](https://lab.arts.ac.uk/books/physical-computing/page/making-a-capacitive-touch-sensor) is that the object you touched doesn't need to be conductive as it is sensing force.

It is cheap and easy to use. It provides accurate readings for physical pressure but it cannot be used for measuring weight. You can put it underneath most materials, e.g. painting, shoes etc, and it is easy to hide.

# Wiring
Wiring up the sensor is simple, the sensor is unpolarized so it's doesn't matter which pin to 5V or GND.

1. Power (one end to 5V)
1. Ground (one end to GND with 10K resistor)
1. Signal (GND side to A0)

![image](https://github.com/creativetechnologylab/physicalComputingTutorials/assets/64136454/a9afec4d-ac96-4449-9b2e-40695f4eb87a)
# Getting started

This example turns on the built-in LED when touched lightly.

````
int sensorPin = A0; 
int sensorValue; 

//sensor value range: 0-1023
//200 is light touch 
//500 is medium touch
//800 is hard touch 
int limit = 200; 

void setup() {
 Serial.begin(9600);
 pinMode(13, OUTPUT);
}

void loop() {

 sensorValue = analogRead(sensorPin); 
 Serial.print("Force Level: ");
 Serial.println(sensorValue);
 
 if (sensorValue > limit) {
 digitalWrite(13, HIGH); 
 }
 else {
 digitalWrite(13, LOW); 
 }
 
 delay(100); 
}
````
