One of the secrets of Arduino Leonardo is the built-in USB MIDI support.

This is really useful for sending data from Arduino to applications like MadMapper, Max and Ableton Live.

In order to use this you'll need to follow the guide on [How to install libraries](https://github.com/creativetechnologylab/physicalComputingTutorials/blob/main/How%20to%20install%20libraries.md) to install the MIDIUSB library. 

The following is a modification of the basic MIDIUSB write example, by wrapping the `noteOn` and `noteOff` code in logic you could attach this to a button or sensor.

````
#include "MIDIUSB.h"

void setup() {
  Serial.begin(115200);
}

void loop() {
  Serial.println("Sending note on");
  noteOn(0, 48, 64);   // Channel 0, middle C, normal velocity
  MidiUSB.flush();
  delay(500);

  Serial.println("Sending note off");
  noteOff(0, 48, 64);  // Channel 0, middle C, normal velocity
  MidiUSB.flush();
  delay(1500);

  // controlChange(0, 10, 65); // Set the value of controller 10 on channel 0 to 65
}

void noteOn(byte channel, byte pitch, byte velocity) {
  midiEventPacket_t noteOn = {0x09, 0x90 | channel, pitch, velocity};
  MidiUSB.sendMIDI(noteOn);
}

void noteOff(byte channel, byte pitch, byte velocity) {
  midiEventPacket_t noteOff = {0x08, 0x80 | channel, pitch, velocity};
  MidiUSB.sendMIDI(noteOff);
}

void controlChange(byte channel, byte control, byte value) {
  midiEventPacket_t event = {0x0B, 0xB0 | channel, control, value};
  MidiUSB.sendMIDI(event);
}
````
