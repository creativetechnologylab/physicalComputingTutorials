# What is a rotary encoder?
A rotary encoder is a device used to measure the rotation of something, similar to a rotary potentiometer but not limited to how many rotations can be made, a common example of a rotary encoder is the volume dial on a car radio, which can be turned infinitely but still only goes from 0 to 100% volume.

Rotary encoders come in a number of different types, typically either with or without 'detents' that is physical feedback as the encoder rotates, and in varying levels of resolution for more or less precise applications.

# Wiring
Wiring is simple...

There are four wires:

1. Ground
2. 5V
3. A switch
4. B switch

![IMG_0048.jpg](https://lab.arts.ac.uk/uploads/images/gallery/2018-05-May/scaled-840-0/IMG_0048.jpg)

# Getting started
Rotary encoders work using two switches which are operated slightly out of phase, meaning that in one direction switch A then B pulse from LOW to HIGH, and in the other direction switch B then A pulse LOW then HIGH, enabling you to detect both that a pulse happened i.e. that it was rotated, but also in which direction.

## Basic Example
In this basic example the encoder outputs the value as a positive or negative number from it's starting position.

````
#define enc1A_pin 2
#define enc1B_pin 3

boolean enc1A_prev;
boolean enc1B_prev;

long enc1 = 0;
long prev_enc1 = 0;

void setup() {
  pinMode( enc1A_pin, INPUT_PULLUP );
  pinMode( enc1B_pin, INPUT_PULLUP );
  Serial.begin( 9600 );
}

void loop() {
  boolean enc1A = !digitalRead( enc1A_pin );
  boolean enc1B = !digitalRead( enc1B_pin );
  
  if ( enc1A_prev == 0 && enc1A == 1 && enc1B_prev == 1 && enc1B == 1 ) enc1++;
  else if ( enc1A_prev == 1 && enc1A == 1 && enc1B_prev == 0 && enc1B == 1 ) enc1--;
  
  if ( prev_enc1 != enc1 ) {
    Serial.println( enc1 );
  }

  if ( enc1A_prev != enc1A ) enc1A_prev = enc1A;
  if ( enc1B_prev != enc1B ) enc1B_prev = enc1B;
  
  prev_enc1 = enc1;
}
````
