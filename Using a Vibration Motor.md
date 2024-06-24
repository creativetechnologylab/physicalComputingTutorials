# What is a vibration motor?
A vibration motor is a DC motor in a compact size that is used to inform the users by vibrating on receiving signals. It is commonly found inside a mobile phone. The one that is available in the lab is coin vibration motor. 

![image](https://github.com/creativetechnologylab/physicalComputingTutorials/assets/64136454/9ae8effc-7892-4dcc-93a9-dced73973ed4)

It requires more current than an Arduino pin can provide, so a transistor is needed to **switch the motor current on and off**. Any NPN transistor can be used. In this tutorial, we are using 2N2222.  The diode acts as a **surge protector** against voltage spikes that the motor may produce. The 0.1µF capacitor **absorbs voltage spikes** produced when the brushes, which are contacts connecting electric current to the motor windings, open and close. To make sure that **not too much current** flows from the output of the transistor, we place a 1KΩ (or up to 5KΩ) in series with the base of the transistor.

# Wiring
These are the electronics used in the circuit.
1. vibration motor
1. 2N2222 transistor (or any other NPN transistor)
1. 0.1µF capacitor
1. 1N4001 diode
1. 1KΩ resistor

It is quite a complex circuit but try your best to follow!

<p class="callout info"><em>Other NPN transistors</em><br />You can use other NPN transistors for this tutorial, BUT, they may have a different pinout with 2N2222. Check the pinout of your transistor and make sure the pins go as the following.
<br />
<br />1. Emitter (E) to Ground (GND)
<br />2. Base (B) to Data pin (pin 3) with 1KΩ resistor
<br />3. Collector (C) to Ground of the actuator (black wire of the motor) 
</p>

![image](https://github.com/creativetechnologylab/physicalComputingTutorials/assets/64136454/8a53ce91-29e1-48f8-9842-1494073fdb88)

# Getting started
This code is getting the motor to vibrate for 1 second and stop for 1 second.

````
int motorPin = 3; //motor transistor is connected to pin 3

void setup()
{
  pinMode(motorPin, OUTPUT);
}

void loop()
{
  digitalWrite(motorPin, HIGH); //vibrate
  delay(1000);  // delay one second
  digitalWrite(motorPin, LOW);  //stop vibrating
  delay(1000); //wait 50 seconds.
}
````
