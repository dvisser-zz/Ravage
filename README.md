# RavAGE - A Toyota 4AGE specific hardware solution for FreeEMS.

### Introduction

The name "RavAGE" is something relating to the Toyota 4-'AGE' engine. The aim of
the RavAGE project is to create a hardware solution for FreeEMS that caters to
the needs of the Toyota 4AGE engines (16V and 20V). It may also be used on most
4/6cyl engine setups with minimal to no modifications required. 

Please see [FreeEMS.org](http://freeems.org) for the most up to date information
and links for this project and all of the other aspects of the FreeEMS project.

### Goals

Core IO specs:

 - 1 FTDI USB (bus powered) communications that are opto coupled to the CPU. 
 - 3 RPM/Position inputs via MAX99xx devices to take advantage of the 3 in the 4AGE CAS assemblies.
 - 8 Standard 'CORE' analogue inputs. 
 - 6 ignition drives (external igniters ONLY).
 - 6 injector drives (high-z ONLY).
 - 5 Ground connections (ECU GND, INJ GND, IGN GND, ACC GND and Analogue Input GND).
 - 3 "12V" connections (+12V CONSTANT,+12V SWITCHED for BRV and key-on signal and +12V ACC for accessory functions).
 - 3 overkill relay drive's (FAN RELAY, FUEL PUMP RELAY and VVT SOLENOID).
 - 1 switched +5V output for TPS and EXT MAP.
 - 2 outputs suitable for driving a 3-wire Toyota Idle Speed Control Valve (+12V ACC, PWM Non-Inverted and PWM Inverted).
 - 2 spare digital inputs.
 - 2 spare analogue inputs (option to configure as temperature or voltage input).
 - 2 spare low side drives.

PCB Size is to be as small as possible, but attention must be paid when choosing
a connector as this will more than likely be the deciding factor on the overall
size. Worst-case scenario will be a PCB that is 100mm x 80mm, which is still
small and allows for the use of some sort of "nice" connector. It could be
made smaller, but at this size, there will be room for extra general purpose
output drivers, analogue inputs, etc.

### Status

For the most up to date status information for the project, refer to the TODO.md
file which is maintained in sync with the schematics by a small team who verify
each other's work.

### Changes

Please send any changes that you make to RavAGE back upstream to [Dan Visser's copy](https://github.com/dvisser/Ravage)

