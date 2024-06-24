# What is the Bare Conductive Touch Board?
The Bare Conductive Touch Board is a board made by Bare Conductive. The Touch Board has 12 capacitive electrodes that respond to a touch. These electrodes can be extended with conductive materials, like Electric Paint or foil. The Touch Board has on-board MP3 playback and a MIDI synthesizer. This means you can either play MP3 files or simulate a MIDI instrument by touching the electrodes.
![image](https://github.com/creativetechnologylab/physicalComputingTutorials/assets/64136454/e9c49db6-010a-419f-8c55-5ef14014be2c)
In short, the Touch Board is a pre-built Arduino that combines the functions of [play MP3](https://lab.arts.ac.uk/books/physical-computing/page/using-a-sparkfun-mp3-trigger) and [capacitive touch sensing](https://lab.arts.ac.uk/books/physical-computing/page/making-a-capacitive-touch-sensor), but you can do more than that. If you don't have the Touch Board, you can still do the same things following the above two tutorials.

## Hardware Plugin
Whenever we use an Arduino, we have to tell the Arduino IDE which Arduino board we are using, whether it is an Arduino Leonardo or Arduino Mega. So we have to do the same here, telling Arduino IDE which board we are using. In this case, the Bare Conductive Touch Board. However, you cannot find the Touch Board from `Tools - Boards`. We have to download and put the plugin in place.

1. **Quit Arduino** if you have it opened.
2. Download the Hardware Plugin here:
[bare-conductive-arduino-public.zip](https://lab.arts.ac.uk/attachments/41)
3. Create a `hardware` folder

	**Windows:**  `Libraries/Documents/Arduino/hardware`
		
    **OR** `My Documents/Arduino/hardware`
	
    **Mac:** `Documents/Arduino/hardware`
	
	**Linux** (Ubuntu): `Home/Arduino/hardware`
4. Unzip and put the folder inside the **hardware** folder

Now open Arduino IDE, you will see the Touch Board from `Tools - Boards - Bare Conductive Boards`.

![image](https://github.com/creativetechnologylab/physicalComputingTutorials/assets/64136454/f7ae7c74-235d-4c8d-9d90-dfc400592072)

## Library
The **MPR121** is the capacitive touch chip on the Touch Board - this library allows us to access it. The **VS1053 chip** is the MP3 chip on the Touch Board. It uses two libraries, one for the chip and one for the onboard micro SD card. 

1. **Quit Arduino** if you have it opened.

2. Download the **MPR121** Library here:
[mpr121-public.zip](https://lab.arts.ac.uk/attachments/40)
1. Download the **VS1053** Library here:
[Sparkfun-MP3-Player-Shield-Arduino-Library-master.zip](https://lab.arts.ac.uk/attachments/39)

3. Go to the `libraries` folder

	**Windows:**  *Libraries/Documents/Arduino/libraries*
		
        
    **OR** *My Documents/Arduino/libraries*

	
    **Mac:** *Documents/Arduino/libraries*
	
	**Linux** (Ubuntu): *Home/Arduino/libraries*
    
4. Unzip **mpr121-public.zip** and find the folder `MPR121` 
4. Unzip **Sparkfun-MP3-Player-Shield-Arduino-Library-master.zip** and find the folders: `SdFat` and `SFEMP3Shield`.
5. Copy `MPR121`, `SdFat` and `SFEMP3Shield` Folder to the **libraries** folder

Now the software Arduino IDE is ready, you will see the libraries from `Sketch - Include Library`.

## File naming
Files saved in the Micro SD card should be named TRACK000.mp3 through TRACK011.mp3, and the Bare Conductive Board will match the file name to the `E0` to `E11` pins and play the according sound files.

<p class="callout info">The Touch Board will work with any size micro SD card up to <b>32GB</b>.
  <br>Make sure your new SD card is formatted as <b>FAT32</b>.</p>


## Wiring
**No wiring is needed.** But you can extend each touch point with wires or connect them to any conductive materials, e.g. fruit.

## Basic Example
This basic example will play TRACK000.mp3 to TRACK011.mp3 from the SD card when the according pin is touched.
Download here: [touch-mp3-public.zip](https://lab.arts.ac.uk/attachments/38)

## Sample MP3 files
To help you get up and running quickly there are some example MP3's you can use.

[Example MP3 Files](https://lab.arts.ac.uk/attachments/46)

## Resources

- [RS Setup Guide](https://docs.rs-online.com/dd48/0900766b8143c704.pdf)
