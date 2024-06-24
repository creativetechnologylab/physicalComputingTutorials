# What is a PIR sensor?
PIR stands for Passive Infra Red and therefore a PIR sensor can etect movement of objects that radiate IR light (like human bodies). It is very commonly used for the security systems.

![image](https://github.com/creativetechnologylab/physicalComputingTutorials/assets/64136454/dec02bb6-34b4-44e9-9ce5-cc810da8c03e)

The HC-SR501’s infrared imaging sensor is an efficient, inexpensive and adjustable module for detecting motion in the environment. The small size and physical design of this module allow you to easily use it in your project.

The output of PIR motion detection sensor can be connected directly to one of the Arduino (or any microcontroller) digital pins. If any motion is detected by the sensor, this pin value will be set to “1”. The two potentiometers on the board allow you to adjust the sensitivity and delay time after detecting a movement.

# Wiring

1. Singal to Pin 3
1. Power to 5V
1. GND to GND

![image](https://github.com/creativetechnologylab/physicalComputingTutorials/assets/64136454/a0654b24-3e17-4f5a-946a-507715649ff4)

# Getting started

````
int ledPin = 13;                // LED 
int pirPin = 3;                 // PIR Out pin 
int pirStat = 0;                   // PIR status
 
void setup() {
  pinMode(ledPin, OUTPUT);     
  pinMode(pirPin, INPUT);     
 
  Serial.begin(9600);
}
 
void loop(){
  
  pirStat = digitalRead(pirPin); 
   
  if (pirStat == HIGH) {            // if motion detected
    digitalWrite(ledPin, HIGH);  // turn LED ON
    Serial.println("Hey I got you!!!");

  } 
  else {
    digitalWrite(ledPin, LOW); // turn LED OFF if we have no motion
   
  }
}
````
