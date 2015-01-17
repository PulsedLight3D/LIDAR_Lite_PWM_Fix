# LIDARLite_PWM_Fix 
A fix for the PWM mode of units shipped prior to January 15, 2015

## Description

**Problem:** Some users have noticed a problem with the PWM read mode of LIDAR-Lite in the 5-6cm range. When an object is in that range it can cause the unit to read a really really really long value that effectively locks up the unit. On Arduino's this produces a "0" value that takes a long time to read. 

**Software Solution:** The software solution for this is to reset the sensor via the PWR_EN line when a zero value is read from the sensor. See details below. 

**Hardware Solution:** If the software solution is not a good fit for your application simply send your unit back to PulsedLight Inc and we'll reprogram it and send it back, please be sure to include a return address. 

PulsedLight Inc.    
P.O. Box 691   
Bend, OR 97709

## Software Solution

### Dependencies
1. Arduino Uno compatible Board
2. Arduino IDE (1.0.6 or newer)
3. USB Cable
4. LIDAR-Lite Sensor made prior to January 15, 2015

### Installation
Download repository, open with Arduino IDE and upload to Arduino

### Arduino Setup

![](http://pulsedlight3d.net/assets.pl3d/llpwmfix.jpg)

#### LIDAR-Lite PWM with PWR_EN setup

LIDAR-Lite Cable|Arduino Pin
:---|:---
5V|5v
PWR_EN|Digital Pin 4
MODE|Connect to 1k ohm resistor and Digital Pin 3
SCL|Unused
SDA|Unused
GND|GND

### Usage
1. Connect to Arduino and upload code
2. Open the serial monitor (make sure the baud rate is set to 9600)
3. The distance will be measured in cm, if a "0" is recieved by the Arduino it will reset the LIDAR-Lite and start reading again (rather than lockup)

