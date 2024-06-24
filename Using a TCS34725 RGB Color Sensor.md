# What is the TCS34725 RGB Color Sensor?
The TCS3472 sensor provides a digital return of red, green, blue (RGB), and clear light sensing values. An RGB Color sensor helps you accurately detect an object’s colour in your Arduino projects.

![image](https://github.com/creativetechnologylab/physicalComputingTutorials/assets/64136454/3ccb9566-a1c2-44dc-851c-87edb0af826f)

# What is I2C?
The TCS34725 has an I2C interface (SDA and SCL) that connects to the Arduino Board. The IC also has an optional interrupt output pin which can be used to interrupt Arduino.

I2C stands for Inter-Integrated Circuit. It is a bus interface connection protocol incorporated into devices for serial communication. I2C Communication Protocol uses only 2 bi-directional open-drain lines for data communication called SDA and SCL. Both these lines are pulled high. Each data bit transferred on SDA line is synchronized by a high to the low pulse of each clock on the SCL line.

1. Serial Data (SDA) – Transfer of data takes place through this pin.
1. Serial Clock (SCL) – It carries the clock signal.

[Learn more about I2C](https://i2c.info/)


## I2C on different Arduino boards
The two major models you can find in Creative Technology Lab are **UNO** and **LEONARDO**. Both have I2C function but have a different pinout. For **UNO**, the SDA pin is A4 and SCL pin is A5. For **LEONARDO**, the SDA pin is SDA(pin 20) and SCL pin is SCL(pin 21).

Not every Arduino model has I2C function and not all of them have the same pinout. Check the model before you hook it up with the TCS34725 sensor. [Learn more](https://www.arduino.cc/reference/en/language/functions/communication/wire/)

# Library
`Adafruit TCS34725` will be used for this tutorial. We have a tutorial on [how to install a library](https://lab.arts.ac.uk/books/physical-computing/page/how-to-install-libraries) here.

# Wiring
For **LEONARDO**, it's more like matching labels.
1. GND - GND
1. VIN - 5V
1. SDA - SDA
1. SCL - SCL

![image](https://github.com/creativetechnologylab/physicalComputingTutorials/assets/64136454/38d05ee0-6ccc-4a14-af32-3eedb525dbe3)

For **UNO**, A4 and A5 are the I2C pins rather than just a Analog Input pin.
1. GND - GND
1. VIN - 5V
1. SDA - A4
1. SCL - A5

![image](https://github.com/creativetechnologylab/physicalComputingTutorials/assets/64136454/7c447425-720a-4b66-8156-1ed0d70b2d46)

# Getting started
After installing the library and wiring the board, go ahead and use the examples in the File > Examples > Adafruit TCS34725 menu in Arduino, the `tcs34725` example is particularly good as it's simple to check it's working.

## Doing more
There is an example in the library for Arduino and Processing which can control the background colour using the colour sensor values.

1. In the File > Examples > Adafruit TCS34725 > `colorview` in Arduino IDE, upload to Arduino.
1. In the File > Examples > Adafruit TCS34725 > examples_processing >  `colorview`  in Arduino IDE, copy and paste in a Processing sketch.

### Serial Port
Before you run the code in Processing, we have to set up the serial port for the communication between Arduino and Processing. Go to line 15.

``
 port = new Serial(this, "COM20", 9600); 
``
"COM20" is the name of the serial port, every USB port on everyone's computer is different. **Replace "COM20" with your own port name.** For me, my port name is *"/dev/cu.usbmodem14601"* so I changed the code like this.
``
 port = new Serial(this, "/dev/cu.usbmodem14601", 9600); 
``

You can find your port name at the bottom of your Arduino IDE or go to Tools > Port > ########(Arduino #####).
![image](https://github.com/creativetechnologylab/physicalComputingTutorials/assets/64136454/dfd065ce-df8c-41e8-9943-0e93e3cb095e)
