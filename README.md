# Craft Store
#### FV-1 based multi-effect development platform that (almost) fits inside 1590b enclosure
Craft Store is a pedalboard friendly implementation of FV-1 with onboard USB programmer.
 <p align="center">
<img src="https://github.com/user-attachments/assets/14b9c65d-9611-478a-afaa-1540e1275c5b" width="500" title="thumbnail">
 </p>
 
---

How it's different
---
On top of the default signal path:
- there's physical feedback loop going from right channel output to the left channel input 
- FV-1's left channel input can be blended into the pedal's output 

Controls:
---
- 0-2 FV-1 potentiometer inputs
- Volume
- mix - full dry to full wet
- clock - 4049 based variable sampling clock 42kHz down to super glitchy 2kHz
- feed - adds FV-1's left channel output to the output signal
- toggle - switches between built-in FV-1 programs and EEPROM
- 8 position program selector


Contents:
---
- [KiCad 8.0 project ](https://github.com/MPrzekop/FV1-Craft-Store/tree/main/Hardware/KiCad)
  - 2 effect boards and optional footswitch doughterboard
<p align="center">
<img src="https://github.com/user-attachments/assets/a25c43ae-9472-415c-ba8d-81efec8f6b78" height="200" title="pcb 3d render">
<img src="https://github.com/user-attachments/assets/a9b1d560-3679-4868-93fa-665ad1c78dac" height="200" title="schematic layout">
<img src="https://github.com/user-attachments/assets/4fafc08a-3b17-4807-a3b0-e0ba4d0cb00f" height="200" title="pcb layout">
 </p>
 
 - [3D printing files ](https://github.com/MPrzekop/FV1-Craft-Store/tree/main/Hardware/3DPrinting)
    - Case and lid, similar to 1590b just 2mm taller 
    - Knobs for 9mm potentiometers V6 is different from V5 that it has an inset to accommodate for 8 position switch thread collar. V5 variants to use depending on filament and printer.
 - [Spincad made example programs ](https://github.com/MPrzekop/FV1-Craft-Store/tree/main/Software)

Build Guide:
---
[BOM](https://github.com/MPrzekop/FV1-Craft-Store/blob/main/Hardware/KiCad/fv1.csv).

Most of the components are SMD so it may require some experience. I've tried to preserve both component ids and values on the PCB itself for ease of build and debugging.

Couple of tips:
- with normal 2.54 sockets and pins the boards may pivot on DC jack, I've soldered sockets when the board was lying on a flat surface to get the most clearance from the pins.
- Clock potentiometer is marked as 100K, this may be excessive as below 20kHz there's an audible hiss. I've tested with 20K and it was more controllable, but still glitchy (theoretically going down to 8kHz). If what you need is longer delays without much audio degradation I'd recommend putting 5K potentiometer there.
- The board stack is slightly too tall for a normal 1590b housing, to make the housing compatible you'll need to file down the lip on the lid, or add around 2mm spacing between the housing and the lid. 
 

Programming Guide:
---

On the board there's a **[ch341a](https://www.wch-ic.com/products/CH341.html)** programmer and **[24lc32](https://ww1.microchip.com/downloads/en/DeviceDoc/21072G.pdf)** EEPROM so any approaches for programming those are valid.
- you'll need drivers from the [ch341a vendor's page](https://www.wch-ic.com/products/CH341.html)
- follow [this tutorial](https://wiki.pedalpcb.com/wiki/Using_the_FV1Dev_on_Microsoft_Windows) for how to program the EEPROM

Creating programs:
---

[Best place to start](https://electric-canary.com/fv1start.html)

- The easiest way, by a mile, is to use [SpinCAD designer](https://github.com/HolyCityAudio/SpinCAD-Designer) 

<p align="center">
<img src="https://github.com/HolyCityAudio/SpinCAD-Designer/raw/master/spincad.png" a="https://github.com/HolyCityAudio/SpinCAD-Designer" height="200" title="spincad">
</p>

- [SpinASM](https://spinsemi.com/products.html), FV-1 flavoured assembly 

<p align="center">
<img src="https://electric-canary.com/images/volume-control.svg?crc=3913409478" height="200" title="pcb 3d render">
</p>

