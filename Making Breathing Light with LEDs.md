# What is an LED?
LED (Light Emitting Diode) is a semiconductor light source that emits light when current flows through it. LED includes two pins, Cathode(-), aka the short leg, and Anode(+), aka the longer leg. It is one of the most common components. Making it lights up is usually the first step into physical computing but we are going to do a little bit more this time.

## What is PWM pin?
Pulse-width modulation (PWM) pins are the pins that you can find on your Arduino with "~" in front of it. For example, pin D3, D5, D6, D9, D10 and D11 on Arduino UNO are PWM pins. The Arduino IDE has a built in function “analogWrite()” which can be used to generate a PWM signal. The frequency of this generated signal for most pins will be about 490Hz and we can give the value from 0-255 using this function.

1. **analogWrite(0)** means a signal of 0% duty cycle. *(turns something off)*
1. **analogWrite(127)** means a signal of 50% duty cycle. *(turns something half on, e.g. dimmed light)*
1. **analogWrite(255)** means a signal of 100% duty cycle. *(turns something on)*

It can be used in controlling the brightness of LED, speed control of a DC motor, controlling a servo motor or where you have to get analog output with digital means.

In this tutorial, we will use the PWM pins to control it and have it perform in breathing light. The second LED in this tutorial is optional.

# Wiring
Wiring is simple, there are just 2 wires and a resistor.

1. LED short pin (-) to Ground
2. LED long pin (+) to PWM Digital pin (D3), via 220Ω resistor

![image](https://github.com/creativetechnologylab/physicalComputingTutorials/assets/64136454/03110a2e-267a-48b9-b42f-22d8fb09f3b8)

# Getting started
```c++
#define led 3 //any PWM pins (~)
#define led2 11 //optional 2nd led

int brightness = 0;    // how bright the LED is
int fadeAmount = 5;

void setup() {
  pinMode(led, OUTPUT);
  pinMode(led2, OUTPUT); //optional for 2nd led
}

void loop() {
  //breathing light
  analogWrite(led, brightness);
  analogWrite(led2, brightness); //optional for 2nd led
  
  brightness = brightness + fadeAmount;
  if (brightness <= 0 || brightness >= 255) {
    fadeAmount = -fadeAmount;
  }
  delay(50); //speed of the pulsing
}

```
