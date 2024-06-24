# What is the Sound Detector?
The Sound Detector is a board made by Sparkfun electronics that provides a way to detect ambient sound levels.
![image](https://github.com/creativetechnologylab/physicalComputingTutorials/assets/64136454/85e6886b-c90c-4e3f-b8fd-380f79f55f25)

There are three connections on the board:

- **Audio** - This is the raw audio from the microphone.
- **Envelope** - This is a analog value representing the volume of the ambient sound.
- **Gate** - This is a digital value representing if sound levels are low or high.

# Wiring
There are two options for wiring, you can use both at the same time:

## Digital
Wired up in digital mode the sound detector signals if the sound level is low with a `LOW` signal, and high with a `HIGH` signal.

This method requires:

1. Power (VCC to 5V)
2. Ground (GND to GND)
3. Gate to a digital pin on the Arduino (yellow wire in the diagram)

There are three wires:
![image](https://github.com/creativetechnologylab/physicalComputingTutorials/assets/64136454/c589ad40-c593-4cee-83d4-8af12211c318)


## Analog
Wired up in analog mode the sound detector provides voltage proportional to the sound level.

This method requires:

1. Power (VCC to 5V)
2. Ground (GND to GND)
3. Envelope to a analog pin on the Arduino (turquoise wire in the diagram)

There are three wires:

![image](https://github.com/creativetechnologylab/physicalComputingTutorials/assets/64136454/43b8ebc6-3e55-4843-80fc-7538ef609b29)



# Getting started
Once wired, the code is that of a standard `digitalRead` or `analogRead` to obtain the value.

## Example code reading envelope

````
#define envelopePin A0

void setup() {
  Serial.begin( 9600 );
  pinMode( envelopePin, INPUT );
}

void loop() {
  Serial.println( analogRead( envelopePin ) );
}
````

## Example code reading gate

````
#define gatePin 2

void setup() {
  Serial.begin( 9600 );
  pinMode( gatePin, INPUT );
}

void loop() {
  Serial.println( digitalRead( gatePin ) );
}
````

# Resources

- [Sparkfun Hookup Guide](https://learn.sparkfun.com/tutorials/sound-detector-hookup-guide?_ga=2.37488355.2109147645.1494246671-1774741291.1490963851)
