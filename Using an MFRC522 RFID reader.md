# What is an MFRC522 RFID reader
RFID means radio-frequency identification. RFID uses electromagnetic fields to transfer data over short distances. RFID is useful to identify people, to make transactions, etc…

You can use an RFID system to open a door. For example, only the person with the right information on his card is allowed to enter. An RFID system uses tags with each identification and a two-way radio transmitter-receiver as a reader.

![image](https://github.com/creativetechnologylab/physicalComputingTutorials/assets/64136454/aedb217d-7e64-498a-a881-36e6b46c3fac)

## Wiring
<p class="callout danger"><b>Caution</b><br />
  You must power this device to 3.3V! This tutorial is based on Arduino UNO, if you are using a different module, please check the specific pinout of that model.
</p>

1. SDA - Digital 10 (SS)
1. SCK - Digital 13 (SCK)
1. MOSI - Digital 11 (MOSI)
1. MISO - Digital 12 (MISO)
1. IRQ (unconnected)
1. GND - GND (Ground)
1. RST - Digital 9
1. 3.3V to 3.3V (Power)

![image](https://github.com/creativetechnologylab/physicalComputingTutorials/assets/64136454/fb0c67ab-9237-453f-9315-92f142c65c18)

## Library

We will be using the `MFRC522` library. Please see this [tutorial](https://github.com/creativetechnologylab/physicalComputingTutorials/blob/main/How%20to%20install%20libraries.md) to learn how to install libraries.

## Getting started
We will be using the example code, `DumpInfo`, from the library to **read** an RFID Tag.

````
#include <SPI.h>
#include <MFRC522.h>

#define RST_PIN         9          // Configurable, see typical pin layout above
#define SS_PIN          10         // Configurable, see typical pin layout above

MFRC522 mfrc522(SS_PIN, RST_PIN);  // Create MFRC522 instance

void setup() {
	Serial.begin(9600);		// Initialize serial communications with the PC
	while (!Serial);		// Do nothing if no serial port is opened (added for Arduinos based on ATMEGA32U4)
	SPI.begin();			// Init SPI bus
	mfrc522.PCD_Init();		// Init MFRC522
	delay(4);				// Optional delay. Some board do need more time after init to be ready, see Readme
	mfrc522.PCD_DumpVersionToSerial();	// Show details of PCD - MFRC522 Card Reader details
	Serial.println(F("Scan PICC to see UID, SAK, type, and data blocks..."));
}

void loop() {
	// Reset the loop if no new card is present on the sensor/reader. This saves the entire process when idle.
	if ( ! mfrc522.PICC_IsNewCardPresent()) {
		return;
	}

	// Select one of the cards
	if ( ! mfrc522.PICC_ReadCardSerial()) {
		return;
	}

	// Dump debug info about the card; PICC_HaltA() is automatically called
	mfrc522.PICC_DumpToSerial(&(mfrc522.uid));
}
````

We will be using the example code, `DumpInfo`, from the library to **read** an RFID Tag.
