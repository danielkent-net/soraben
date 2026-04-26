![Soraben Logo](img/logo.png)
# Soraben Build Instructions

Building your very own Soraben is doable for anyone that has the tools and
expertise for soldering fine surface mount components. **Experience with reflow
soldering techniques is highly recommended.** A solder reflow oven will make
the job much easier, but it should be possible with a hot air rework station
or a hotplate.

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

[The exported BOM can be found in the repository](https://github.com/danielkent-net/soraben/blob/main/pcb/bom/bom.csv). A simplified list
[can be found below](#full-bill-of-materials). The [HTML BOM](https://github.com/danielkent-net/soraben/blob/main/pcb/bom/ibom.html) is also very useful for sourcing and assembly.

To simplify the BOM, you can use a 50V 0.1uF 0805 capacitor for both C1 and C7.

Technically, if you are only interested in a subset of the overall functionality,
you can omit certain components to reduce cost and simplify the build:

| Functionality | Components          |
|:-------------:|:-------------------:|
| 24V Fan       | Relay (K1), 4-Pin Port (J1), Schottky Diodes (D3, D4), R8, MOSFET (Q2) |
| 24V LED       | R4, R5, R6, R7, 6-pin Port (J3) |

3. A compatible Sensiron SEN6x sensor

Currently, I recommend purchasing the **SEN66** for 3D print monitoring unless
you are printing with a material that can release or otherwise decompose into
formaldehyde, in which case you should consider the SEN68 or SEN69C (both
are unreleased as of writing). If you are not planning to monitor for VOCs,
the **SEN63C** is less expensive (though it has a less accurate CO2 sensor).
If you are just interested in particulate, the **SEN62** is currently the
least expensive option. Here is a full table of SEN6x sensors, their
capabilities, and their price as of writing:

| Sensor | PM | RH+T | VOC | NOx | CO₂ | HCHO |  Price (Digikey, USD<sup>1</sup>) |
|--------|:--:|:----:|:---:|:---:|:---:|:----:|:---:|
| SEN50 |   ✓   |       |      |     |    |      |   $20.91  |
| SEN54 |   ✓    |   ✓    |   ✓   |     |    |      |   $26.85  |
| SEN55 |    ✓   |   ✓    |   ✓   |   ✓  |    |      |  $30.59   |
| SEN62  | ✓  |  ✓   |     |     |     |      | $19.45 | 
| SEN63C | ✓  |  ✓   |     |     |  ✓  |      | $30.58 | 
| SEN65  | ✓  |  ✓   |  ✓  |  ✓  |     |      | $26.86 | 
| SEN66  | ✓  |  ✓   |  ✓  |  ✓  |  ✓  |      | $58.53 | 
| SEN68  | ✓  |  ✓   |  ✓  |  ✓  |     |  ✓   | N/A<sup>2</sup> | 
| SEN69C | ✓  |  ✓   |  ✓  |  ✓  |  ✓  |  ✓   | N/A<sup>2</sup> | 

<sup>1</sup> Does not include tariffs

<sup>2</sup> Not yet listed on Digikey or Mouser

4. JST-GH and JST-SH Cable Supplies

You can either buy pre-crimped cabling from Amazon/AliExpress/etc, or buy
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

6. Multimeter

A multimeter is very important for testing the board, as well as
checking the values of components if they happen to get mixed together.
If you are doing any kind of electrical or electronics work, you should
already have a multimeter, or consider purchasing a good quality one for this
and future projects.

7. (Optional, Highly Recommended) Benchtop Power Supply

A benchtop power supply will allow you to test the assembled PCB for shorts
and other problems by setting a low current limit. A benchtop power supply
can also act as a known good stand-in supply if you are having trouble with
transient power issues from lower-quality AC to DC adapters, and can also 
be used to directly power different voltage rails on a PCB if you think
the circuit for generating the power rail is not working.

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
| 24V Power Supply                 |                        | 1        |
| JST-PH 6-Pin Header, Right Angle |                        | 1        |
| JST-PH 6-Pin Header, Vertical    |                        | 1        |
| JST-PH 4-Pin Header, Vertical    |                        | 1        |
| JST-SH 4-Pin Header (Qwiic)      |                        | 1        |
| JST-GH to JST-PH 6 Pin Cable     |                        | 1        |
| JST-PH 6 Pin Cable               |                        | 1        |
| JST-PH 4 Pin Cable               |                        | 1        |
| M2 Heat Inserts (Case Only)      |                        | 4        |
| M3 Heat Inserts (Case Only)      |                        | 2        |
| M2 Screws, XXmm                  |                        | 4        |
| M3 Screws, XXmm                  |                        | 2        |

## Assembly Instructions

### Step 1: Prepare Your Workspace

Make sure you have your PCB, components, tools, and solder accessible and
organized before you begin assembly. I personally sort each component type into
a grid on my solder mat, and then print a legend that I place nearby so I know
which component is in which grid.

### Step 2: Apply Solder Paste

Carefully align your solder stencil on top of the PCB. I strongly recommend
3D printing a jig to help align the stencil and provide extra surface to
securely attach it to a surface; an example PCB jig
[can be found in this repository](https://github.com/danielkent-net/soraben/blob/main/cad/)

### Step 3: Place Surface Mount Components

I recommend placing components in an order that roughly follows component
type and component value. I also strongly recommend
[downloading the HTML BOM to help you assemble the board](https://github.com/danielkent-net/soraben/blob/main/pcb/bom/ibom.html)

This is the order that I used:

U1 (Voltage Converter)
C1 (0.1u 16V)
C7 (0.1u 50V)
C5, C6 (10u 50V)
C2, C3, C8, C9 (22u 16V)
C4 (47u 6.3x7.7)
L1 (Inductor)
Q1 (2-Channel N-MOSFET)
Q2 (1-Channel SOT-323 N-MOSFET)
R1 (30Ω)
R2 (30.9kΩ)
R3, R5, R7, R8 (10kΩ)
R4, R6 (10Ω)
R9, R10, R11, R12 (4.7kΩ)
D1 (24V TVS)
D2 (3v3 TVS)
D3, D4 (Schottky, 0603)

### Step 4: Peform Reflow Soldering

Insert the board into the reflow oven and configure the reflow profile to
match the type of solder paste you used. Wait patiently while the reflow
completes and for your board to cool afterwards. Carefully inspect your board
for any misaligned parts, and use a hot air rework station to correct any
parts that did not reflow correctly.

### Step 5: Solder Testing-Critical Through-Hole Components

For testing the board without risking the higher-cost components, we will now
solder on just the 20-pin sockets, and optionally the barrel plug if you have
a barrel plug to terminal block adapter. If you do not have a barrel plug to
terminal block adapter, carefully and lightly solder on some wires to the
marked positive and negative pins on the barrel jack footprint. Use enough
solder to 

**Make sure when soldering the sockets that they are aligned and straight!**
If the sockets are at an angle, you may not be able to physically insert the
Pi Pico W later! If you have a Pico W with presoldered headers, you can fit
the sockets onto the headers, then fit the headers into the Soraben PCB, then
solder on each of the pins. You should be able to remove the Pico W from the
header sockets once they have been soldered to the PCB. If your Pico W does
not have presoldered headers, I recommend inserting the header pins into a
breadboard and using that as an alignment jig to solder the header pins to your
Pi Pico W.

### Step 6: Connectivity and Power On Tests

While this step is technically optional, I highly recommend testing the board
before socketing in a Pi Pico W in case something went wrong. You don't want to
fry a microcontroller or any other components!

First, check for dead shorts on the board using a multimeter configured for
resistance (audible tone mode if your multimeter supports it). Using the test
pads on the bottom, make sure that there are no shorts between ground and
any of the test points on the board. If there are any shorts, **do not plug
in power to your board!**.

If you have a benchtop power supply with a configurable current limiter, set
the output voltage to the same voltage of your power supply, or as high as
possible otherwise (the buck converter is rated for 4.5-28VDC, and the design
has been tested on 12, 16, and 24VDC). Set the current limit to 5mA. **Do not
activate the voltage output yet.**

Insert a high-resistance (10k is fine) resistor between the second and third
pins in the row from the left (the Soraben PCB connectors should be on top,
with the footprint for the relay on the left).

At this point, you can activate the voltage output. You should see the voltage
output stabilize to your power supply's configured voltage. If the voltage is
lower, then there is a short and you should disable power output immediately.

While activated, set your multimeter and carefully probe TP1 (the 3v3 rail).
You should see a voltage output of around 3.3 volts.

If you found no shorts and the 3v3 rail was correct, the board should be ready
for the rest of the through hole components. 

### Step 7: Solder Through-Hole Components

Using a soldering iron, attach the remaining through hole components. Make sure
that components are soldered securely with no cold joints, but also try to avoid
overheating components like the relay that might get damaged if overheated, or
the plastic-coated parts like the ports.

### Step 8: Fabricate Cables and Connectors

Next, you will need to fabricate cables to attach your BentoBox fans, the SEN6x,
and your LED strip to Soraben. I have found that using pre-crimped cables for
each and soldering them to existing wires is generally easier than crimping
JST pins to existing wires, but you should cover the wires in heat-shrink
tubing to prevent shorts.

### Step 9: Flash and Install Pi Pico W

A working ESPHome YAML configuration [can be found in this repository](https://github.com/danielkent-net/soraben/tree/main/esphome). Note that as of writing there are a few
functions and features not yet included in the base ESPHome release that make
the Soraben work better, and are included in the YAML file as external components.
Versions newer than 2026.3.0 may not require the external components; if you
encounter compilation errors, try removing the `external_components` block,
lines 18-24. Also make sure you have a
[properly formatted `secrets.yaml` file](https://esphome.io/guides/security_best_practices/#using-secretsyaml)
in the same directory as the `firmware.yaml` file.

To build your firmware, download [ESPHome](https://esphome.io/) or use the
Home Assistant ESPHome App to build a firmware image. I generally install
and use ESPHome through `pip` in a virtual environment:

```sh
python3 -m venv venv
./venv/bin/activate
pip install esphome
esphome compile projects/firmware.yaml
```

To flash your firmware, with your Raspberry Pi Pico W powered off and unplugged
from your PC, hold the reset button while plugging the Pico into your PC.
You should see an "RPI-RP2" external drive appear. On newer versions of ESPHome,
you can use the `esphome run firmware.yaml` file to automatically upload the
firmware over USB to the Pico. Alternatively, you can manually copy the
`firmware.uf2` file to the RPI-RP2 device (generally this file is located at
`.esphome/build/soraben/.pioenvs/soraben/firmware.uf2`, relative to where the
`firmware.yaml` file from this repository is located). Once the file is copied
and the RPI-RP2 device disappears, the firware has been flashed, and the
Pico W can be socketed into Soraben's MCU socket.

Typically, ESPHome should be able to push updated firmware to Soraben's onboard
Pi Pico W through Wi-Fi; however, if that process fails for any reason, you can
remove the Pi Pico W from the socket and use the initial flashing procedure
to flash updated firmware.

You can optionally develop your own software to use with Soraben. Relevant
pinouts are as follows:

| GPIO | Pin | Function           |
|:----:|:---:|:------------------:|
| 0    | 1   | Fan Relay          |
| 18   | 24  | I2C1 SDA (External)|
| 19   | 25  | I2C1 SCL (External)|
| 20   | 26  | I2C0 SDA (SEN6x)   |
| 21   | 27  | I2C0 SCL (SEN6x)   |
| 27   | 32  | Warm White LED PWM |
| 28   | 34  | Cool White LED PWM |

### Step 9: Build Case

The 3D CAD files for the prototype case [can be found in the repository](https://github.com/danielkent-net/soraben/tree/main/cad). This design should be fairly easy to print on most FDM 3D printers using standard materials at a standard 0.2mm layer height.
I used inexpensive PETG to print mine. You
can also get a 3D printing service to print a case if you do not have access to
a 3D printer. Note that the lid uses a 3D printing technique called a
"sacrificial layer" for the two screw holes; you should be able to punch a hole
in these layers by pushing a hex wrench or even the screw itself through this
hole.

Once you have your case, use a soldering iron or other tool to insert the M2
and M3 heat inserts into their respective locations. Then, insert the Soraben
into the slot, and attach it to the case using four M2 screws. Insert your
SEN6x sensor into the slot and connect the cable to the Soraben board. Then, 
connect the fan header to the fan plug through the side hole. Finally, put
the lid on and secure the lid using the two M3 screws.

If you wish to design your own case, you can export an STL of the Soraben
PCB from KiCad to use for your own design. The spacing of the M2 mounting
holes are 78.6mm lengthwise and 31.6mm widthwise.



