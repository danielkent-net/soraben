![Soraben Logo](img/logo.png)
# Soraben Build Instructions

Building your very own Soraben is doable for anyone that has the tools and
expertise for soldering fine surface mount components. **Experience with reflow
soldering techniques is highly recommended.** A solder reflow oven will make
the job much easier, but it should be possible with a hot air rework station
and/or a hotplate.

## Parts and Supplies

To build a Soraben, you will need to source the following parts and supplies:

1. A Soraben PCB and (optional) Solder Stencil

Getting a Soraben PCB is likely the easiest part, especially if you purchase
from [OSH Park](https://oshpark.com) (not sponsored, I just use them for most
of my prototype PCBs, and have been happy with their quality, price, and
customer service). Currently, the boards cost $25 for 3 on their normal
2-layer service (~$8.33 each), or 20 for $100 ($5 each). With OSH Park, you
can simply upload the [`soraben.kicad_pcb`](https://github.com/danielkent-net/soraben/blob/main/pcb/soraben.kicad_pcb) file to fabricate the board.

If you plan to use a different PCB fabricator that doesn't support direct
KiCad PCB import, you will need to download the Soraben project files,
open the PCB, and export the Gerber files that the PCB fabricator requires.

If you are planning to perform reflow soldering, a stencil mask will make the
process much easier. I used [OSH Stencils](https://www.oshstencils.com/)
for producing my stencils for Soraben and other projects (again, not sponsored,
just a customer), but there are other options including DIY options if you own
a suitable laser cutter.

2. The Soraben PCB components

[See the full bill of materials for the PCB components.]()

3. A compatible Sensiron SEN6x sensor

Currently, I recommend purchasing the **SEN66** for 3D print monitoring unless
you are printing with a material that can release or otherwise decompose into
formaldehyde, in which case you should consider the SEN68 or SEN69C (both
are unrelease as of writing). If you are not planning to monitor for VOCs,
the **SEN63C** is less expensive (though it has a less accurate CO2 sensor).
If you are just interested in particulate, the **SEN62** is currently the
least expensive option. Here is a full table of SEN6x sensors, their
capabilities, and their price as of writing:

| Sensor | PM | RH+T | VOC | NOx | CO₂ | HCHO |  Price (Digikey, USD^1) |
|--------|:--:|:----:|:---:|:---:|:---:|:----:|:---:|
| SEN50 |   ✓   |       |      |     |    |      |   $20.91  |
| SEN54 |   ✓    |   ✓    |   ✓   |     |    |      |   $26.85  |
| SEN55 |    ✓   |   ✓    |   ✓   |   ✓  |    |      |  $30.59   |
| SEN62  | ✓  |  ✓   |     |     |     |      | $19.45 | 
| SEN63C | ✓  |  ✓   |     |     |  ✓  |      | $30.58 | 
| SEN65  | ✓  |  ✓   |  ✓  |  ✓  |     |      | $26.86 | 
| SEN66  | ✓  |  ✓   |  ✓  |  ✓  |  ✓  |      | $58.53 | 
| SEN68  | ✓  |  ✓   |  ✓  |  ✓  |     |  ✓   | N/A^2 | 
| SEN69C | ✓  |  ✓   |  ✓  |  ✓  |  ✓  |  ✓   | N/A^2 | 

^1 Does not include tariffs

^2 Not yet listed on Digikey or Mouser

4. JST-GH and JST-SH Cable Supplies

You can either buy pre-crimped cabling from Amazon/AliExpress/etc., or buy
a crimper, ends, and suitable wire. Currently, you will need at a minimum a
6-pin JST-SH to JST-GH cable for the Soraben to SEN6x cable. If you plan to
connect an LED strip, you will need to fabricate or solder on a 6-pin JST-SH
cable.

5. Solder

You will need solder to connect all the components on the PCB. As stated
previously, I highly recommend using reflow based soldering techniques for
all surface mount components, either with a reflow oven (most recommended) or
a hotplate and/or hot air rework station (less recommended).
Through hole components can be soldered using a soldering iron.

I used Chip-Quik TS391SN thermally-stable lead free solder for this project.
If your solder reflow oven doesn't get quite that hot, you can either get
lower temperature lead-free solder or get leaded solder if you're willing to
use leaded solder.


## Full Bill of Materials

| Part                             | Size/Part Number       | Quantity |
|----------------------------------|------------------------|----------|
| PCB                              | N/A                    | 1        |
| Solder Stencil                   | N/A                    | 1        |
| Raspberry Pi Pico W              | SC0918                 | 1        |
| 20-Pin 2.54mm Socket Headers     | 61302011821            | 2        |
| C, 47µF 50V, 6.3x7.7             | UCD1H470MCL1GS         | 1        |
| C, 10µF 50V                      | Generic 0805           | 2        |
| C, 0.1µF 50V                     | Generic 0805           | 1        |
| C, 22uF, 16V                     | Generic 0805           | 4        |
| C, 0.1µF, 16V                    | Generic 0805           | 1        |
| L, 4.7uH                         | INDPM3015X150N         | 1        |
| R, 10Ω                           | Generic 0603           | 2        |
| R, 30Ω                           | Generic 0603           | 1        |
| R, 4.7kΩ                         | Generic 0603           | 4        |
| R, 10kΩ                          | Generic 0603           | 4        |
| R, 30.9k                         | Generic Thin Film 0603 | 1        |
| 3V Relay                         | Panasonic DK1A-3V-F    | 1        |
| Schottky Diode, 40V              | Generic 0603           | 2        |
| 3.3V TVS Diode                   | Generic SOD-323        | 1        |
| 24V TVS Diode                    | Generic SOD-323        | 1        |
| N-MOSFET                         | Generic SOT-323        | 1        |
| 2-Channel N-MOSFET               | DMN3032LFDBQ-13        | 1        |
| Voltage Regulator 4.5-28V        | TPS56339DDCR           | 1        |
| Barrel Jack                      | Same Sky PJ-002A       | 1        |
| JST-PH 6-Pin Header, Right Angle |                        | 1        |
| JST-PH 6-Pin Header, Vertical    |                        | 1        |
| JST-PH 4-Pin Header, Vertical    |                        | 1        |
| JST-SH 4-Pin Header (Qwiic)      |                        | 1        |
| JST-GH to JST-PH 6 Pin Cable     |                        | 1        |
| JST-PH 6 Pin Cable               |                        | 1        |
| JST-PH 4 Pin Cable               |                        | 1        |




![Soraben, fully assembled.](img/full.jpg)                              
Soraben is a smart device designed to allow automation of a 3D printer filter
such as the [BentoBox](https://www.printables.com/model/272525), using an
RP2040-based Raspberry Pi Pico (W) microcontroller at its core. Soraben
also includes a dedicated connector for a Sensiron SEN6x air quality sensor,
enabling both monitoring and automation of the filter, printer, or anything
else based on those sensor readins. Soraben also has optional connectors for
dual-color LED strips, and a JST-SH Qwiic-compatible connector for attaching
additional sensors, all powered through a single 24VDC input. Soraben's    
firmware is based on ESPHome, allowing its software to be upgraded, extended,
and repurposed.

ound
et/projects/posts/20260328-soraben.html).

This repository contains the KiCad design files, bill of materials, and 3D
printable enclosure for Soraben. 

# Making Your Own
![Soraben PCB Render](img/render.png)
I had my bare Soraben PCBs fabricated at [OSH Park](https://oshpark.com/). To
order at OSH Park, upload `pcb/soraben.kicad_pcb` to the OSH Park website and
follow their instructions.

For any other PCB fab, download the project files and use KiCad to generate
the Gerber files required for fabrication. You will need to add the project
symbols and footprints (both custom and the ki-lime-pi-to-go libraries)
to your project files.

I strongly suggest ordering a solder stencil and using a PCB reflow oven to
assemble the board. You can hand solder the through-hole components afterwards.

To build the firmware, use ESPHome (command line or web-based firmware builder)
to compile a `firmware.uf2` file. Then, connect the Raspberry Pi Pico W to your
computer via Micro-USB **while holding the reset button**. You can then use
`esphome upload` to automatically copy the firmware file, or you can manually
copy the generated `firmware.uf2` file to the RPI-RP2 drive on your computer.
All updates except for the initial flash can be performed over-the-air (OTA).

# License
The KiCad project files are licensed under the CERN OHL-S V2 license. You are
free to share and remix this design provided you abide by the terms of the
license, which may require you to share your design files and provide
attribution to me.

The 3D printable 3MF files are dual licensed under the CERN OHL-S V2 license
and the Creative Commons 4.0 Attribution-ShareAlike license.

The [ki-lime-pi-to-go library](https://github.com/recursivenomad/ki-lime-pi-to-go)
for Raspberry Pi Pico footprints is available from the original author under
the MIT-0 license.

