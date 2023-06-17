# MSM501-Firmware
Firmware for MSM501-MainsReciprocalCounter. 

## Overview
This is the firmware for MSM501-Mains Reciprocal Counters.  
Find the hardware and documentation in this [repository](https://github.com/ndornseif/MSM501-MainsReciprocalCounter).  
This is just an Arduino script you can upload using the official Arduino IDE.  
Hardware and software are built around an Arduino Nano.   
Measurement results are in uHz and sent out over serial on header J2.  
They are sent as ASCII and separated by LF and CR.   
Default parameters: 115200 baud, 8 data, 1 stop, no parity  
You can use this [serial logger](https://github.com/ndornseif/Serial-Logger) for saving the output to a file.  

## Example output
```
50020548\r\n
50032928\r\n
```

## Configuration
Change constant `defaultGateTime` to vary the measurement time (value in ms).  
A shorter measurement time lowers effective resolution but increases the update rate.  


Change the constant `refClockFrequency` to the reference clock frequency (in uHz) you are using.  
The reference can be supplied externally via BNC (CN2) or from the reference oscillator (X1).  

Change the constant `correctionOffset` to a offset applied to the reference frequency (in uHz).  
If you dont know your clock offset set this value to zero.  
See the section "Calibration" of this document on more info on how to determine the offset.  

## Calibration
1. Remove the link on JMP1 (J3).
2. Apply a calibration frequency to the center pin of J3.
The calibration frequency must be a 0 - 5V square wave.  
Preferably 50Hz or 60Hz and 50% duty cycle.  
3. Record the the measured frequency of the MSM501.
4. Calculate the offset as follows:  
All values should be entered in uHz.  
Where f<sub>ref</sub> is the nominal reference frequency,  
f<sub>cal</sub> the applied calibration frequency and f<sub>measured</sub> the recorded measurement result.  
$correctionOffset = f_ref - \frac{f_ref}{f_cal \div f_measured}$  
5. Enter the offset into the firmware.

## Other
Published under GPL-3.0 license.  
