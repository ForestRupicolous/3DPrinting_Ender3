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

PlatformIO USB access: https://docs.platformio.org/en/latest/faq.html#platformio-udev-rules
Restart OS afterwards!
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
Ender 3 PSU support 
https://www.thingiverse.com/thing:3023240  




### Planned
https://www.youtube.com/watch?v=fq2IKp3jeaY  
https://www.thingiverse.com/thing:3014930  
https://www.thingiverse.com/thing:2759439  
https://www.thingiverse.com/thing:3030151  
https://www.thingiverse.com/thing:2987100


## 2022: Upgrade to SKR mini E3 V1.2 with BL Touch
BIGTREETECH-SKR-mini-E3 repo downloaded
Build SW with platformio (in VS Code)

## Slicer
Links and Logs to used Slicer settings
Important start gcode:  
_G28; Home axis_  
_M420 S1; Load leveling mesh_  

## Bed Leveling:
2020-09-22:
Export from Repetier Host:
22:24:55.009 : echo:Marlin 1.1.9
22:24:55.009 : echo: Last Updated: 2018-08-01 | Author: (MartinKorinek, Ender-3)
22:24:55.009 : echo:Compiled: May 28 2020
22:24:55.009 : echo: Free Memory: 11619  PlannerBufferBytes: 1232
22:24:55.039 : echo:V55 stored settings retrieved (655 bytes; crc 50763)
22:24:55.039 : echo:  G21    ; (mm)
22:24:55.039 : echo:  M149 C ; Units in Celsius
22:24:55.039 : echo:Filament settings: Disabled
22:24:55.039 : echo:  M200 D1.75
22:24:55.040 : echo:  M200 D0
22:24:55.040 : echo:Steps per unit:
22:24:55.040 : echo:  M92 X80.00 Y80.00 Z400.00 E95.00
22:24:55.040 : echo:Maximum feedrates (units/s):
22:24:55.040 : echo:  M203 X500.00 Y500.00 Z12.00 E120.00
22:24:55.041 : echo:Maximum Acceleration (units/s2):
22:24:55.041 : echo:  M201 X9000 Y9000 Z500 E10000
22:24:55.041 : echo:Acceleration (units/s2): P<print_accel> R<retract_accel> T<travel_accel>
22:24:55.079 : echo:  M204 P500.00 R1500.00 T500.00
22:24:55.080 : echo:Advanced: Q<min_segment_time_us> S<min_feedrate> T<min_travel_feedrate> X<max_x_jerk> Y<max_y_jerk> Z<max_z_jerk> E<max_e_jerk>
22:24:55.080 : echo:  M205 Q20000 S0.00 T0.00 X10.00 Y10.00 Z0.20 E2.50
22:24:55.080 : echo:Home offset:
22:24:55.080 : echo:  M206 X0.00 Y0.00 Z0.00
22:24:55.080 : echo:Mesh Bed Leveling:
22:24:55.081 : echo:  M420 S0 Z0.00
22:24:55.081 : echo:  G29 S3 X1 Y1 Z0.77500
22:24:55.081 : echo:  G29 S3 X2 Y1 Z0.95000
22:24:55.081 : echo:  G29 S3 X3 Y1 Z1.25000
22:24:55.081 : echo:  G29 S3 X1 Y2 Z0.87500
22:24:55.081 : echo:  G29 S3 X2 Y2 Z1.07500
22:24:55.082 : echo:  G29 S3 X3 Y2 Z1.25000
22:24:55.082 : echo:  G29 S3 X1 Y3 Z1.05000
22:24:55.112 : echo:  G29 S3 X2 Y3 Z1.15000
22:24:55.112 : echo:  G29 S3 X3 Y3 Z1.10000
22:24:55.112 : echo:Material heatup parameters:
22:24:55.112 : echo:  M145 S0 H185 B45 F255
22:24:55.112 : echo:  M145 S1 H215 B0 F255
22:24:55.112 : echo:PID settings:
22:24:55.112 : echo:  M301 P21.73 I1.54 D76.55
22:24:55.591 : FIRMWARE_NAME:Marlin 1.1.9 (Github) SOURCE_CODE_URL:https://github.com/MarlinFirmware/Marlin PROTOCOL_VERSION:1.0 MACHINE_TYPE:Ender-3 EXTRUDER_COUNT:1 UUID:cede2a2f-41a2-4748-9b12-c55c62f367ff
22:24:55.591 : Cap:SERIAL_XON_XOFF:0
22:24:55.592 : Cap:EEPROM:1
22:24:55.592 : Cap:VOLUMETRIC:1
22:24:55.594 : Cap:AUTOREPORT_TEMP:1
22:24:55.594 : Cap:PROGRESS:0
22:24:55.594 : Cap:PRINT_JOB:1
22:24:55.594 : Cap:AUTOLEVEL:0
22:24:55.594 : Cap:Z_PROBE:0
22:24:55.594 : Cap:LEVELING_DATA:1
22:24:55.594 : Cap:BUILD_PERCENT:0
22:24:55.594 : Cap:SOFTWARE_POWER:0
22:24:55.594 : Cap:TOGGLE_LIGHTS:0
22:24:55.594 : Cap:CASE_LIGHT_BRIGHTNESS:0
22:24:55.594 : Cap:EMERGENCY_PARSER:0
22:24:55.594 : Cap:AUTOREPORT_SD_STATUS:0
22:24:55.597 : Cap:THERMAL_PROTECTION:1
22:24:55.646 : X:0.00 Y:0.00 Z:0.00 E:0.00 Count X:0 Y:0 Z:0
22:24:55.668 : echo:DEBUG:INFO,ERRORS
22:24:55.668 : echo:Active Extruder: 0
22:24:55.668 : Begin file list
22:24:55.674 : End file list
22:24:55.674 : echo:Unknown command: "M80"
22:24:55.676 : echo:DEBUG:INFO,ERRORS
22:24:55.676 : echo:Active Extruder: 0

22:42:44.729 : 0        1        2
22:42:44.729 : 0 +0.77500 +0.95000 +1.25000
22:42:44.729 : 1 +0.87500 +1.07500 +1.25000
22:42:44.729 : 2 +1.05000 +1.15000 +1.10000

## Filaments
3DEE PLA 
+Good color and good printing experience
~Cartboard box
-No vacuum seal or silica gel
-One clog due to thick part in filament (spliced together?)
