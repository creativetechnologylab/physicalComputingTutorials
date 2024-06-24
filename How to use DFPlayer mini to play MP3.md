# What is a DFPlayer?
The DFPlayer Mini MP3 Player For Arduino is a small and low-priced MP3 module with a simplified output directly to the speaker. The module can be used as a stand-alone module with an attached battery, speaker and push buttons or used in combination with an Arduino UNO or any other with RX/TX capabilities.
[Know More](https://wiki.dfrobot.com/DFPlayer_Mini_SKU_DFR0299#target_0)

![image](https://github.com/creativetechnologylab/physicalComputingTutorials/assets/64136454/b59a20aa-8cb4-445d-b309-c8496ef8b5c3)

# Wiring
Wiring up the sensor is quite complex, the pins are not labelled so you will have to refer to the pinout.
![image](https://github.com/creativetechnologylab/physicalComputingTutorials/assets/64136454/3fd99334-fdcc-445f-aa53-7f26a9dd9563)

##### DFplayer Mini Wiring
1. VCC to 5V (Power)
1. RX to D2 via 1K resistor
1. TX to D3
1. SPK_1 to Speaker(+) *red wire*
1. GND to GND (Ground)
1. SPK_2 to Speaker(-) *black wire*

##### potentiometer Wiring
1. right pin to 5V (Power)
1. middle pin to A0 (Signal)
1. left pin to GND (Ground)
![image](https://github.com/creativetechnologylab/physicalComputingTutorials/assets/64136454/dc7c3efc-70c8-477e-a132-54f5e7dee8b0)


# File handling
The order you copy the mp3 onto the micro SD card will affect the order mp3 played, which means the `play(1)` function will play the first mp3 copied into the micro SD card.

<p class="callout warning"> <b>MAC User Attention!</b><br / > If you are using Mac OS X to copy the mp3, the file system will automatically add hidden files like: "._0001.mp3" for index, which this module will handle as valid mp3 files.<br / ></p>

It is really annoying. To remove them, follow the below steps:

1. Finder - Go to your USB drive
2. Press `Shift` + `Command` + `.` to reveal all hidden files
3. Select all `.XXXXXX` files and directories and delete
4. Empty Bin
5. Eject your USB drive


# Library
`DFRobotDFPlayerMini` library will be used for this module. We have a tutorial on [how to install a library](https://lab.arts.ac.uk/books/physical-computing/page/how-to-install-libraries) here.

# Get Started
In this example, we are using the potentiometer to control two audios. It will play the first audio when the potentiometer turns to the right and play the second when it turns to the left.

<p class="callout warning"> <b>DF layer will not initiate!</b><br / > If you didn't put in the SD card, or have no MP3 files in the SD card, the module will not work. Make sure you are using .mp3, not .wav or any other audio formats.<br / ></p>

````
#include "SoftwareSerial.h"
#include "DFRobotDFPlayerMini.h"

// Use pins 2 and 3 to communicate with DFPlayer Mini
static const uint8_t PIN_MP3_TX = 2; // Connects to module's RX
static const uint8_t PIN_MP3_RX = 3; // Connects to module's TX
SoftwareSerial softwareSerial(PIN_MP3_RX, PIN_MP3_TX);

const int pot = A0;
int potValue = 0;

// Create the Player object
DFRobotDFPlayerMini player;

void setup() {

  pinMode(pot, INPUT);

  // Init USB serial port for debugging
  Serial.begin(9600);
  // Init serial port for DFPlayer Mini
  softwareSerial.begin(9600);

  // Start communication with DFPlayer Mini
  if (player.begin(softwareSerial)) {
    Serial.println("OK");

    // Set volume to maximum (0 to 30).
    player.volume(30);
  } else {
    Serial.println("Connecting to DFPlayer Mini failed!");
  }      
}

void loop() {

	potValue = analogRead(pot);

	if(potValue > 500 ){ 

	 static unsigned long timer = millis();
 	 if (millis() - timer > 2000) { //2000 is the duration of the audio(1)
  		timer = millis();

   		//(2) is the 2rd file in the sd card, the order = the order you copied the file to it
   		player.play(2);  
  }
  
	}else {
  	  static unsigned long timer = millis();
  
 	 if (millis() - timer > 3000) { //3000 is the duration of the audio(2)
  	  	timer = millis();
   		player.play(1); 
  		}
	}
}
````
