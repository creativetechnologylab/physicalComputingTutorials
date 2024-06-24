# What is the MPR121?
The MPR121 is a tiny microchip formerly manufactured by NXP, now under Resurgent Semiconductor, it is a tiny surface mount device that provides 12 capacitive touch electrodes through an I2C interface.

# What is capacitive touch?
Capacitive touch the the technology used on modern touch sensitive devices such as phone and tablet screens, trackpads and computer mice like Apple's Magic Mouse.

Capacitive touch takes advantage of the human body being electrically conductive, this is why using a pen on a smart phone doesn't work and styluses for these devices are made of metal so they will make an electrical connection.

Capacitive touch is relatively complex to understand but fundamentally the sensor can detect when you are in proximity or actually touching the electrode, or any conductive part between the chip and the end of the wire.

If you extend a wire from the electrode, even if it is shielded with plastic, it will probably detect you touching the wire just the same as the exposed metal part.

# Different versions of MPR121
The first common use of the MPR121 in physical computing was the now discontinued Sparkfun MPR121 breakout, this is the most commonly available version in the here at LCC.

MPR121 breakouts from Adafruit and Seedstudio also exist, and we've begin replacing our Sparkfun boards with Adafruit as the Sparkfun boards break and need replacing.

Additionally the MPR121 is used in the Bare Conductive Touch Board which is effectively an Arduino Leonardo with an MPR121 and MP3/WAV/OGG/MIDI player (similar to the Sparkfun MP3 Trigger) integrated one board.

## Key differences

### Sparkfun MPR121

- Power input: 3.3V only! **5V is the primary reason these break**.
- Address: 0x5A is the default address, changing this requires alterations to the board

### Adafruit MPR121
- Power input: 3.3V to 5V
- Address: 0x5A, it is also relatively easy to configure the address to 0x5B, 0x5C or 0x5D allowing up to 48 electrodes (12 x 4).

# Wiring
Wiring is pretty simple, it's an I2C component so it's relatively standard.

<p class="callout danger"><em>Warning</em><br />The Sparkfun MPR121 is a 3.3V device, do not connect the power pins to 5V, you will instantly destroy the board.</p>

<p class="callout info"><em>Older Arduino boards</em><br />Some older Arduino boards do not have SDA and SCL pins as shown in the diagrams, in this case you'll need to look it up on the boards documentation, however most Arduino boards used A4 as SDA and A4 as SCL.</p>

## Sparkfun MPR121

[![sparkfun MPR121.png](https://lab.arts.ac.uk/uploads/images/gallery/2022-09/scaled-1680-/yUWE3Oyzt7WzNqFw-sparkfun-mpr121.png)](https://lab.arts.ac.uk/uploads/images/gallery/2022-09/yUWE3Oyzt7WzNqFw-sparkfun-mpr121.png)

## Adafruit MPR121

[![Adafruit MPR121.png](https://lab.arts.ac.uk/uploads/images/gallery/2022-09/scaled-1680-/rW1dzc1b0EmcVtOu-adafruit-mpr121.png)](https://lab.arts.ac.uk/uploads/images/gallery/2022-09/rW1dzc1b0EmcVtOu-adafruit-mpr121.png)
# Library
Adafruit, Sparkfun, Seeedstudio and Bare Conductive all provide Arduino libraries, however by far the best which includes tools for visualising the data is the [Bare Conductive Touch Board library](https://github.com/BareConductive/mpr121) and [grapher](https://github.com/BareConductive/mpr121-grapher). All libraries should all work interchangeably as long as you get the correct address and IRQ pin.

The key thing to remember when using examples from the Bare Conductive library is that they use the address `0x5C` rather than the default `0x5A` address used on both the Sparkfun and Adafruit boards, also ensure that you use the correct IRQ pin based on the example you are using.

We have a tutorial on [how to install a library](https://lab.arts.ac.uk/books/prototyping-lab/page/how-to-install-libraries) here.

# Getting started
After installing the library and wiring the board, go ahead and use the examples in the File > Examples menu in Arduino, the Simple Touch example is particularly good as it's simple to check it's working.

## Basic Example
This is a basic example of using the MPR121 with the Bare Conductive MPR121 library to get the proximity value and touch status, this can easily be extrapolated into a project.

[Sketch: Basic Example](https://gist.github.com/unknowndomain/9d7122a5beb44b5b3ebf6c8a4928fdfd)

## CSV Example
This is an example using the MPR121 with the Bare Conductive MPR121 library to output each electrode's touch status to the serial port as a comma separated string.

This example can be modified to work with MaxMSP easily by changing the delimiter line to a space instead of a comma:

    #define DELIMITER " "
    
You could also modify this example to output the proximity data, instead of the touch data by modifying the `updateTouchData` line to:

    MPR121.updateFilteredData();

And the `getTouchData` line to:

    Serial.print( MPR121.getFilteredData( i ) );
 
[Sketch: CSV Example](https://gist.github.com/unknowndomain/66d566eb655fc3ebdd4f)
