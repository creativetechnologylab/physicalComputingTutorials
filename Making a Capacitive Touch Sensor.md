# What is Capacitive Touch Sensing?
Simply put, it is the touch sensing of all conductive materials including tinfoil, banana, plant, pencil drawing etc. In this tutorial, we will show you two types of Capacitive Touch Sensing: acute touch and proximity. 

# Library
`ADCTouch` will be used for acute touching. It provided the best accuracy without ANY external hardware. 

`CapacitiveSensor` library will be used for proximity and/or acute touching. However, due to the constraint of the physical circuit, reading might be sometimes unreliable.

We have a tutorial on [how to install a library](https://github.com/creativetechnologylab/physicalComputingTutorials/blob/main/How%20to%20install%20libraries.md) here.

# ADCTouch Library
This library makes use of the AVR internal wiring to get decent resolution with just a single pin.
## Wiring  
Wiring is super simple with 1 wire:
1. jumper wire to A0, another end with a piece of tin foil

![image](https://github.com/creativetechnologylab/physicalComputingTutorials/assets/64136454/9dda678e-136e-4195-ae88-e2783c9aafa7)

## Code

````c++
#include <ADCTouch.h>

#define TOUCHPIN A0

// set the touch sensor resolution: 
// higher means more stable results, at the cost of higher processing times
#define RESOLUTION 100

#define SMOOTH 100 // determine how many readings are stored for smoothing
float multiplier = 1.2; // determine when the sensor is understood as "ON"
int previousReadings[SMOOTH]; // smooth data a little: the last readings
int currentIndex = 0; // used for cycling through the array
int reading; // the latest reading

// calculate the average of the previous readings
int average(){
  unsigned long sum = 0;
  for(int i = 0; i < SMOOTH; i++){
    sum += previousReadings[i];
  }
  return sum / SMOOTH;
}


void setup() {
  Serial.begin(9600); // serial communication
  pinMode(13,OUTPUT);
  // fill the [previousReaings] array with readings
  for(int i = 0; i < SMOOTH; i++){
    previousReadings[i] = ADCTouch.read(TOUCHPIN, RESOLUTION);
  }
}

void loop() {
  
  reading = ADCTouch.read(TOUCHPIN, RESOLUTION); // read the sensor
  Serial.println(reading);
  
  // check if triggered
  if(reading > average() * multiplier){
     digitalWrite(13, HIGH);
  }else{
    digitalWrite(13, LOW);
    previousReadings[currentIndex] = reading;
    
    // set index for the next reading
    currentIndex++;
    
    // mnake sure [currentIndex] doesn't get out of bounds
    if(currentIndex >= SMOOTH){
      currentIndex = 0;
    }
 } 
}

````
To use this code you will need the [ADCTouch Library](https://github.com/martin2250/ADCTouch).

# CapacitiveSensor Library
The physical setup includes a medium to high value (100K ohm - 50M ohm) resistor between the send pin and the receive (sensor) pin. The receive pin is the sensor terminal. A wire connected to this pin with a piece of foil at the end makes a good sensor.
## Wiring  
1. 10M ohm resistor between pin2 and pin4
2. 1 wire to pin2 to tinfoil

![image](https://github.com/creativetechnologylab/physicalComputingTutorials/assets/64136454/835c2dca-1bb6-4bcd-8f82-0dd5a3c2e36a)
## Code

````c++
#include <CapacitiveSensor.h>

CapacitiveSensor   cs_4_2 = CapacitiveSensor(4,2);        // 10M resistor between pins 4 & 2, pin 2 is sensor pin, add a wire and or foil if desired

void setup()                    
{
   cs_4_2.set_CS_AutocaL_Millis(0xFFFFFFFF);     // turn off autocalibrate on channel 1 - just as an example
   Serial.begin(9600);
}

void loop()                    
{
    long start = millis();
    long total1 =  cs_4_2.capacitiveSensor(30);

    Serial.print(millis() - start);        // check on performance in milliseconds
    Serial.print("\t");                    // tab character for debug windown spacing

    Serial.println(total1);                  // print sensor output 1

    delay(10);                             // arbitrary delay to limit data to serial port 
}
````
To use this code you will need the [CapacitiveSensor Library](https://github.com/PaulStoffregen/CapacitiveSensor).
