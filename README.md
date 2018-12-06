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
https://www.thingiverse.com/thing:2994683
https://www.thingiverse.com/thing:3015832
https://www.thingiverse.com/thing:2935204
https://www.thingiverse.com/thing:2550255
LCD Knob



### Planned
https://www.youtube.com/watch?v=fq2IKp3jeaY
https://www.thingiverse.com/thing:3014930
https://www.thingiverse.com/thing:2759439



## Slicer
Links and Logs to used Slicer settings
Important start gcode:
_G28; Home axis_
_M420 S1; Load leveling mesh_
