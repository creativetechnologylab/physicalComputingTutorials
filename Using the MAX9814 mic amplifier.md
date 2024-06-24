This Adafruit MAX9814 microphone amplifier allows you to easily detect sound.

There are a total of five connections on this mic, however we will only be using VCC, GND and OUT in our wiring. You can read more about this component [here](https://cdn-learn.adafruit.com/downloads/pdf/adafruit-agc-electret-microphone-amplifier-max9814.pdf).

## Wiring 

1. Power (VCC to 3.3V)
2. Ground (GND to GND)
3. Output to analog pin on the Arduino (OUT to A0)

There are three wires:

![image](https://github.com/creativetechnologylab/physicalComputingTutorials/assets/64136454/2d470c51-bece-43ad-9ad9-325162773fdd)

## Retrieving Data 

This code allows instructs the mic to detect and prints out values corresponding to the sound's varying volume.

```c++
int MicPin = A0; 
int MicVolume = 0; // Define a variable MicVolume and initialize it to 0

void setup() {
    Serial.begin(115200); // Initialize serial communication
}

void loop() {
    MicVolume = analogRead(MicPin); 
    Serial.println(MicVolume);
}
```

You can check that your circuit is working by looking at the Serial Plotter; In the menu bar go to Tools &gt; Serial Plotter or press Command + Shift + L on your keyboard. Make sure this is set to 115200 baud.

![image](https://github.com/creativetechnologylab/physicalComputingTutorials/assets/64136454/3ab5bcb0-69fd-45b3-904e-ff0c301065d0)

To utilise this data, you can temporarily slow down the data coming in from the mic and look to the **Serial Monitor** this time, to set up your own threshold, e.g. :

```c++
void loop() {
    MicVolume = analogRead(MicPin); 
    
    if (MicVolume > 400) { // If the volume is above this threshold a warning comes up in the Serial Monitor
      Serial.println("Loud noise");
      delay(500);
    } else {
    Serial.println(MicVolume); 
    }
}
```
