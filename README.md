pimatic-athome-arduino
======================

##Overview

This is the Arduino source code to communicate with the [pimatic-athome plugin](https://github.com/dfischbach/pimatic-athome).

As hardware two [JeeNodes](http://jeelabs.net/projects/hardware/wiki/JeeNode) from [JEELABS](http://jeelabs.org) are used ([available here](http://www.digitalsmarties.net/products/jeenode)). A JeeNode is a Arduino compatible micro-controller board (ATMega328P), which has a RFM12B wireless RF module already on board.

The first JeeNode(receiver) is connected with a FTDI USB/serial adapter to an USB port of the Raspberry Pi or a MacBook. It can control 868MHz based protocols like FS20 with the RFM12B module. A 433MHz transmitter and receiver module is connected to control Elro switches or receive signals from an Elro remote control.

The second JeeNode(transmitter) has an ultrasonic sensor attached to measure the amount of water in a well. Temperature is measured with Dallas DS18B20 sensors, which are connected over OneWire.
The JeeNode measures the values and sends them wireless to the first JeeNode.


##Setup

Copy the AtHomeLib folder to the Arduino IDEs library folder. It is no real library but it is used to share the header with the definitions of the wireless network between the sender and the receiver source code.

Other required Arduino libraries:

[JeeLib](https://github.com/jcw/jeelib) : support for the JeeNodes and the wireless radio modules

[SerialCommand](https://github.com/kroimon/Arduino-SerialCommand): tokenize and parse commands received over the serial port

[RCSwitch](https://code.google.com/p/rc-switch/): operate remote radio controlled devices 315/433MHz

[OneWire](http://www.pjrc.com/teensy/td_libs_OneWire.html): support for the 1-wire bus

[DallasTemperature](http://milesburton.com/Main_Page?title=Dallas_Temperature_Control_Library): support for Dallas 1-Wire temperature devices


Modify the source code for your needs, e.g. use only one microcontroller to periodically send test values.

![Transmitter](https://github.com/dfischbach/pimatic-athome-arduino/blob/master/Doc/AtHome%20Transmitter.png?raw=true)


![Receiver](https://github.com/dfischbach/pimatic-athome-arduino/blob/master/Doc/AtHome%20Receiver.png?raw=true)

