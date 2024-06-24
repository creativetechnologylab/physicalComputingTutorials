# What is Neopixel?
Neopixel is a name given by Adafruit. Neopixel is an addressable LED, meaning that it can be programmed individually. With the library created by Adafruit, you can easily program the Neopixel strip for your project. They come in different sizes and shapes and you can shorten or lengthen them flexibly. Once set up, they are very durable and efficient. They are commonly found in a lot of house decorations or light installations.

![image](https://github.com/creativetechnologylab/physicalComputingTutorials/assets/64136454/c4ddc8ea-7eab-424d-9890-d9c1c2a107d5)

# Wiring

1. DIN to Pin6
1. +5V to 5V
1. GND to GND

![image](https://github.com/creativetechnologylab/physicalComputingTutorials/assets/64136454/a4204c8d-7834-4274-bcce-43c9c96c7ada)

# Library

[Adafruit NeoPixel](https://github.com/adafruit/Adafruit_NeoPixel) library will be used. 
<p class="callout warning">**Warning**<br />Download version 1.9.0 or below for a more stable performance.</p>

We have a tutorial on [how to install a library](https://github.com/creativetechnologylab/physicalComputingTutorials/blob/main/How%20to%20install%20libraries.md) here.

# Getting started
Once the library is installed, you can use the example code for a test run.

![image](https://github.com/creativetechnologylab/physicalComputingTutorials/assets/64136454/3112f39a-3b30-41fc-a240-e334cf436f81)

Before uploading the code to Arduino, one change has to be made.
You should be able to find the below lines in the code.
````
// How many NeoPixels are attached to the Arduino?
#define LED_COUNT 60
````
You have to make sure how many pixels are attached to the Arduino.
For example, if you are using this Neopixel stick with 8 pixels, then you have to change **60** to **8**.

![image](https://github.com/creativetechnologylab/physicalComputingTutorials/assets/64136454/73c3b662-6a35-48c2-ab47-1f7d41183da4)
````
// How many NeoPixels are attached to the Arduino?
#define LED_COUNT 8
````

You should see your Neopixel beamming up right now.
