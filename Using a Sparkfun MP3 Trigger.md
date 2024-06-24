# What is the MP3 Trigger?
The MP3 trigger is a board made by Sparkfun electronics that provides a way to play MP3 files from a Micro SD card via either one of 18 `TRIG` inputs on the board, or serial communication with the board.

The MP3 Trigger has a headphone output which can be connected to powered speakers of your headphones for testing.

# Loading files
You must us a micro SDSC (up to 2GB) card, or a SDHC (up to 32GB) card formatted in FAT16 or FAT32. After inserting the card you must power cycle the MP3 Trigger so it detects the card, this can be done by switching the `USB <-> EXT` switch back and forth.

- **USB**: means power from the Arduino.
- **EXT**: means power via the 2.1mm connector to the left of the switch.
![mp3trigger.png](https://lab.arts.ac.uk/uploads/images/gallery/2022-06/scaled-1680-/mYR7sRfdQBNASacY-mp3trigger.png)

## File naming
Files should be named 001.MP3 through 018.MP3, and the MP3 Trigger will match the file name to the `TRIG` pins, if you controlling the MP3 Trigger via serial the number will match 0 to 255.

# Wiring
Wiring is simple:

There are three wires:

1. Ground (GND connects to GND)
2. Power (USBVCC connects to 5V)
3. Data (RX on the MP3 Trigger to TX on the Arduino)
4. _Optionally you can connect the TX on the MP3 Trigger back to the RX on the Arduino if you wish to get playback status information._

![mp3trigger wiring_bb.png](https://lab.arts.ac.uk/uploads/images/gallery/2022-06/scaled-1680-/VEGKSaEjkUFfoLtM-mp3trigger-wiring-bb.png)

# Getting started
There are libraries available for the Sparkfun MP3 Trigger however it's so easy to use it's easier to use `Serial.print` to control it rather than a library.

## Basic Example
This basic example will play 001.MP3 - 005.MP3 from the SD card with a 1 second delay between playing each.

This is a great demo of how to play files from the SD card via Serial.

<p class="callout warning"> <b>Warning </b><br / >If you are using Mac OS X to copy the mp3, the file system will automatically add hidden files like: "._0001.mp3" for index, which this module will handle as valid mp3 files. It is really annoying. So you can run following command in terminal to eliminate those files.<br / >
</p>
`njkn`

**You will need to replace "Serial" with "Serial1" in the code if you are using Arduino Leonardo!**
````
void setup() {
  // Start the serial port at 38.4K
  Serial.begin( 38400 ); 

  // Set volume
  Serial.print( "v" );
  Serial.write( 0 ); // 0 = maximum volume, 255 = minimum volume
}

void loop() {
  // Loop from 1 to 5
  for ( int i = 1; i <= 5; i++ ) {
    // Play file i ( 1 to 5 )
    Serial.print( "t" );
    Serial.write( i );

    // Wait a bit
    delay( 1000 );
  }
}
````


## Sample MP3 files
To help you get up and running quickly there are 5 example MP3's you can use with the basic example of Tom saying 1-5.

[Example MP3 Files](https://lab.arts.ac.uk/attachments/43)


# Resources

- [Sparkfun Hookup Guide](https://learn.sparkfun.com/tutorials/mp3-trigger-hookup-guide-v24)
