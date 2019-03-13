# 3DPrinting_Ender3
Collection of stuff for Creality Ender 3 3D printer

## Build
Ender 3 with Creality glass bed  
Build using "Precision Alignment Guide" from Luke Hatfield (Thanks!!!) from facebook user group.

## Firmware
Flashed bootloader using Arduino Decimila as ArduinoISP. This needs an 100 Ohm Pull-Up between Arduino RST and 5V otherwise the uploader just finds the Decimila.  
Installed firmeware using this bootloader.  
Currently used Marlin 1.1.9 with configuration taken from https://github.com/wronex/Marlin-Ender-3  
Activated manual mesh leveling with 9 points

## Extruder calibration
Disconnected PTFE tube -> 100 mm result in 96 mm output
M503 shows 93 steps/mm
Original extruder steps/mm value × 100 mm = total steps taken:
93 × 100 = 9300

From that, we can extrapolate that calibrated extruder steps/mm value (y) × actual extruded distance = total steps taken:
y × 96 = 9300

Therefore, calibrated extruder steps/mm value (y) = total steps taken / actual extruded distance:
y = 9300 / 96
= 96.875
Use 
_M92 E96.875_ to upload it
_M500_ to save it
Test it again
See its to much, measure and calculate again
_Set to 95 steps/mm_

Test again at end of tube
change it in Marlin FW!


##Leveling:
Manual mesh bed leving from printer options
* preheat PLA
* Start proccess
* Set z value for all 9 points (paper)
* Store settings!
* Add _M420 S1;_ to start gcode after homing to load stored mesh!   
also see https://www.youtube.com/watch?v=mAU7cIZ0Hns

## Upgrades
Links and log for done upgrades
### Installed
Ender 3 pressure fitting fix 
https://www.thingiverse.com/thing:2994683  
2020 Snap On Filament Guide - Ender 3 / CR-10 
https://www.thingiverse.com/thing:3015832  
Creality Ender 3 board fan guard 
https://www.thingiverse.com/thing:2935204  
Retro feed knob for Anycubic Kossel - Extruder Rotation Visualizer [ERV] 
https://www.thingiverse.com/thing:2550255
The Most Ultimate Creality CR-10/S4/S5/Ender 2/Ender 3/Ender 4 Extruder Upgrade 
https://www.thingiverse.com/thing:2605108  
Ender 3 LCD Cover 
https://www.thingiverse.com/thing:3030151  



### Planned
https://www.youtube.com/watch?v=fq2IKp3jeaY  
https://www.thingiverse.com/thing:3014930  
https://www.thingiverse.com/thing:2759439  
https://www.thingiverse.com/thing:3030151  
https://www.thingiverse.com/thing:2987100


## Slicer
Links and Logs to used Slicer settings
Important start gcode:  
_G28; Home axis_  
_M420 S1; Load leveling mesh_  

## Filaments
3DEE PLA 
+Good color and good printing experience
~Cartboard box
-No vacuum seal or silica gel
-One clog due to thick part in filament (spliced together?)