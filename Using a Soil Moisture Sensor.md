# What is a Soil Moisture Sensor?
The Soil Moisture Sensor measures soil moisture grace to the changes in electrical conductivity of the earth (soil resistance increases with drought).

# Wiring
Wiring up the sensors is simple:

1. Power (VCC to 5V)
1. Ground (GND to GND)
1. Signal (SIG to A0)

![image](https://github.com/creativetechnologylab/physicalComputingTutorials/assets/64136454/127442a2-e12f-41cd-83ef-b9d7f2b21671)

# Getting started

This example turns on the built-in LED when the soil is dry.

````c++
int sensorPin = A0; 
int sensorValue;  
int limit = 300; //300-600 is a good range of moisture generally

void setup() {
 Serial.begin(9600);
 pinMode(13, OUTPUT);
}

void loop() {

 sensorValue = analogRead(sensorPin); 
 Serial.print("Moisture Level: ");
 Serial.println(sensorValue);
 
 if (sensorValue < limit) {
 digitalWrite(13, HIGH); 
 }
 else {
 digitalWrite(13, LOW); 
 }
 
 delay(100); 
}
````
