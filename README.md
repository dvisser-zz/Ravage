# Ravage - A 4AGE specific hardware solution for FreeEMS.

### Introduction

The name "Ravage" is something relating to 4-'AGE'. The aim of the Ravage project
is to create a hardware solution for FreeEMS that caters to the needs of the Toyota
4AGE engines (16V and 20V). It may also be used on most 4 cylinder setups with minimal
to no modifications required. 

Ideally, at the end of the day, I am hoping that future developments in software allow for full sequential injection AND ignition. If PCB size becomes an issue, the bare minimum number of igniter and injector channels will be 4 of each and spare low side drives etc will be removed to make way for these. 

Please see [FreeEMS.org](http://freeems.org) for the most up to date information
and links for this project and all of the other aspects of the FreeEMS project.

### Goals

Core IO specs:

 - 1 FTDI USB (bus powered) + opto couplers for inverter powered laptops 
 - 3 RPM/Position inputs via MAX99xx devices to take advantage of the 3 in the 4AGE CAS assemblies.
 - 8 standard 'core' analogue inputs 
 - 2 ignition drives (driver chips for external igniters, spare 2 channels if space permits)
 - 4 injector drives (high-z, spare 4 channels if space permits)
 - 3 ground "input" connections (CPU GND, INJ GND, ACC GND)
 - 2 "12V" connections (constant CPU power, switched BRV power/key-on signal)
 - 2 overkill relay drive's (fan and fuel pump)
 - 6 (or more) ground output pins for (external MAP, TPS, IAT, CHT, MAT, CAS)
 - 1 switched 5V outputs for TPS

PCB Size is to be as small as possible, but attention must be paid to what connector is chosen as this will more than likely be the deciding factor on the overall size. Worst-case scenario will be a PCB that is 100mm x 80mm, which is still small and allows for the use of some sort of "nice" connector. It could be made smaller, but if I make it 100mm x 80mm then I will have room for extra spare drives, etc. 

### Changes

Please send any changes that you make to Ravage back upstream to [Dan Visser's copy](https://github.com/dvisser/Ravage)

