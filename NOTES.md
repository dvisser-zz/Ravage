# Design Detail Notes

This file is to contain various details that aren't appropriate to show in the
schematic such as default specifications for passive components and deviations
from those defaults.

 - Unless otherwise noted, all resistors to be 1% metal film construction and 100mW power handling.
 - Pull up resistors on thermistor inputs, voltage measurement divider networks, and regulator V setting network to be 0.1% metal film.
 - Capacitors 1.0uF and under to be X7R ceramic, and in very small values, C0G/NP0.
 - All polarised capacitors are tantalumn, 35V minimum when exposed to battery voltage, 10V minimum for internal regulated voltages.
 - VR input resistors to be 200V rated and have a power rating of 500mW or greater. 
 - VR input capacitors must be 200V rated. 
 - VR 5k shunt resistor must be 2W or greater
 - ADC 470R current limiting resistors must be 250mW or greater. 
 - Ignitor drive output 200R current limiting resistors must be 2W or greater. 
 - Ferrite bead to 5V USB input before caps to prevent USB power noise corrupting comms should be something like this: http://nz.element14.com/murata/blm18pg300sn1d/ferrite-bead-0603-case-30ohm/dp/1515741RL
 - Analogue and Digital input schottky diodes are to be BAT721S.

