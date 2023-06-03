# MSM501-Firmware
Firmware for MSM501-MainsReciprocalCounter. 

## Overview
This is the firmware for MSM501-Mains Reciprocal Counters.  
Find the hardware and documentation in this [repository](https://github.com/ndornseif/MSM501-MainsReciprocalCounter).  
This is just an arduino script you can upload using the official Arduino IDE.  
Hardware and software are build around an Arduino nano.   
The measured values are send out as uHz (in ascii) over the serial connection.  
Default baudrate: 115200  

## Configuration
Change constant `defaultGateTime` to vary the measurment time (value in ms).  
A shorter measurement time lowers effective resolution but increases the update rate.  


Change constant `refClockFrequency` to the reference clock frequency (in uHz) you are using.  
The reference can be supplied externaly via BNC (CN2) or from the reference oscillator (X1).  

## Other
Published under GPL-3.0 license.  
