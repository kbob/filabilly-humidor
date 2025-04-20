# FilaBilly Dehumidifier Assembly Guide


## Overview

Welcome to the **FilaBilly Dehumidifier (FBD)**.  This is a compact smart device that extracts water from the air.  It is meant to be used in an airtight cabinet to create a low humidity environment to store 3D printer filament.

This is part of a larger project in progress, the **FilaBilly Humidor (FBH)**.  The FBH is based on the [FilaBilly](https://www.printables.com/model/660713-filabilly-filament-rack).  The FilaBilly turns an IKEA BILLY bookcase into a filament storage cabinet.  The FBH expands on the FilaBilly by sealing the cabinet and adding lighting, environment monitoring and control, and smart home integration.

The FilaBilly Dehumidifier is an ESPHome smart device based on an ESP32 micro controller.  It connects to your network using Wi-Fi.  You can control it directly with a web browser or integrate it into Home Assistant.  In the future, I intend to also be able to monitor and control it from the FilaBilly Humidor's micro controller.

The FilaBilly Dehumidifier includes a printed circuit board for the electronics.  All of the parts use through-holes[^1] for easy assembly, and all of the parts should be easy to source.

[^1]: With one exception. The optional QWIIC connector is surface mount.

The FilaBilly Dehumidifier is closely based on [Ben Krejci's filament dehumidifier](https://www.benkrejci.com/post/dehumidifier).  Ben gets credit for the overall design, the air and water routing through the box, and most of the ESPhome firmware.  I would have just used Ben's design except that he started with a CPU cooler that is no longer made.  So the FilaBilly Dehumidifier is designed to fit the Noctua NH-U9S cooler.

The FilaBilly Dehumidifier is a work in progress.  The mechanical assembly feels finished.  The ESPHome firmware is functional but missing some features.  I intend to design some brackets to clip it onto FilaBilly rails.  And the larger FilaBilly Humidor project is still mostly theoretical at this point.  Still, I'm publishing it in unfinished state because it's good enough to use.


## Bill of Materials

You will need these parts to build the FBD.  The Buy links are representative.  You may have parts on hand; you can certainly find the parts cheaper elsewhere.

### Printed Parts

| Quantity | Name                | Material | Supports? |
|---------:|:--------------------|:---------|:---------:|
|        1 | Housing Left Half   | PETG     |    Yes    |
|        1 | Housing Right Half  | PETG     |    Yes    |
|        1 | HeatsinkDrill Guide | any      |     -     |
|        1 | Bottom Vent Slider  | any      |    Yes    |
|        1 | Electronics Cover   | any      |     -     |
|        1 | PCB Standoff        | any      |     -     |
|        1 | DHT22 Standoff      | any      |     -     |
|        2 | Half Seal           | TPU[^2]  |     -     |

[^2]: The seal halves will work best in TPU, but PETG may work.  They are designed to be deformed a little during assembly.  If you use PETG, you may have to file or trim them to fit.


### PCB Assembly Parts

The FBD includes a custom **printed circuit board (PCB)** to connect the ESP32 micro controller to the rest of the electronics.  This guide assumes you're familiar with the process of ordering PCBs and assembling electronics.  If not, the Internet is full of resources to get you started.

The PCB has space for a QWIIC connector, but it is not used.  If you want to add I²C peripherals such as an alternative humidity sensor, you can populate it.  You're on your own for mechanical packaging and ESPHome configuration if you do, though.

| Quantity | Description                     | Buy |
|---------:|:--------------------------------|:----|
|        1 | Printed Circuit Board           | [OSH Park](https://oshpark.com/shared_projects/0QmItzAm) |
|        1 | MP1584 Regulator Module         | [Amazon](https://www.amazon.com/dp/B08DHS5XVK) |
|        1 | IRLB8721 Power MOSFET           | [Digikey](https://www.digikey.com/en/products/detail/infineon-technologies/irlb8721pbf/2127670) |
|        1 | PJ-102AH Barrel Jack            | [Digikey](https://www.digikey.com/en/products/detail/same-sky-formerly-cui-devices/PJ-102AH/408448) |
|        1 | 2 pos 3.5mm terminal block      | [Digikey](https://www.digikey.com/en/products/detail/w%C3%BCrth-elektronik/691214110002/2508516) |
|        2 | 7 pos female header 2.54mm      | [Digikey](https://www.digikey.com/en/products/detail/sullins-connector-solutions/PPTC071LFBN-RC/810146) |
|        1 | 4 pos male header 2.54mm        | [Digikey](https://www.digikey.com/en/products/detail/sullins-connector-solutions/PREC040SAAN-RC/2774814)<br>(40 pins, cut it to length) |
|        2 | 3 pos male header 2.54mm        | (see above) |
|        4 | 2 pos male heder 2.54mm         | (see above) |
|        1 | 10K 1/4w through hole resistor  | [Digikey](https://www.digikey.com/en/products/detail/stackpole-electronics-inc/CF14JT10K0/1741265) |
|        1 | 4.7K 1/4w through hole resistor | [Digikey](https://www.digikey.com/en/products/detail/stackpole-electronics-inc/CF14JT4K70/1741428) |

#### Optional

If you add the QWIIC connector, you will need these additional parts.

| Quantity | Description                     | Buy |
|---------:|:--------------------------------|:----|
|        2 | additional 4.7K resistors       | (see above) |
|        1 | JST BM04B-SRSS-TB               | [Digikey](https://www.digikey.com/en/products/detail/jst-sales-america-inc/BM04B-SRSS-TB/926696) |


### Other Parts

| Quantity | Description | Buy |
|---------:|:------------|:----|
|        1 | Noctua NH-U9S CPU Cooler          | [Amazon](https://www.amazon.com/dp/B00TBHYYFK) |
|        1 | TEC-12705 Peltier Cooler          | [Amazon](https://www.amazon.com/dp/B09GXDFW39) |
|        1 | aluminum heatsink, 40x40x20mm     | [Amazon](https://www.amazon.com/dp/B07FXP35FW) |
|        1 | thermal paste                     | [Amazon](https://www.amazon.com/dp/B07L9BDY3T/) |
|        1 | Seeed XAIO ESP32C3                | [Seeed Studio](https://www.seeedstudio.com/Seeed-XIAO-ESP32C3-p-5431.html) |
|        1 | DHT22 temperature/humidity module | [Amazon](https://www.amazon.com/dp/B09TKTWXH1) |
|        1 | DS18B20 temperature probe         | [Amazon](https://www.amazon.com/dp/B00M1PM55K) |
|        1 | 12V 5A power supply               | [Amazon](https://www.amazon.com/dp/B0CW2PJQLJ/) |
|        1 | silicone tubing                   | [Amazon](https://www.amazon.com/dp/B0957KZVGG/) |
|        1 | 3 conductor female-female cable   | [Amazon](https://www.amazon.com/dp/B07GD312VG)<br>(tear off three strands) |
|        2 | ferrules, 22awg                   | [Amazon](https://www.amazon.com/dp/B0BJD5796C) |
|        2 | M5 nylon lock nuts                | |
|        2 | M5x30 SHCS machine screws         | |
|        2 | M3x40 SHCS machine screws         | |
|        4 | M3x30 SHCS machine screws         | |
|        5 | M3x16 SHCS machine screws         | |
|        2 | M3x10 SHCS machine screws         | |
|        4 | M3x8 SHCS machine screws          | |
|        2 | M2.5x10 SHCS machine screws       | |


## Parts Preparation

### Deburr the PCB

If the PCB has "mouse bite" burrs around its edges, file them smooth until the PCB fits into the PCB Standoff printed part.


### Remove supports and clean parts

Remove the supports from the printed parts that have them.  The easiest way to clear supports from the tube in the Housing Right Half is to push them out with a long thin screwdriver.

It will also help to run screws through all the screw holes to clean them up until the screws slide through easily.  Don't clean up the blind holes &mdash; the screws need to bite into the plastic there.

Don't forget to clean the M5 holes in the dehumidifier feet.

### Drill heatsink

Use the Heatsink Drill Guide to drill a hole in between the fins of the heatsink.  Drill all the way to the heatsink base, but not beyond.  There is an etched line on the drill guide showing how far to drill.  Test fit the DS18B20 temperature probe and ensure it goes all the way in and contacts the heatsink base.  I used a 15/64" (5.95mm) bit, and I had to wobble it to enlarge the hole.  A 6mm bit would probably be ideal.

### Separate fan from CPU cooler

Unclip the wire clips from the Noctua NH-U9S CPU cooler and remove the fan.  Discard the clips.

### Remove clamp from CPU cooler

Insert a long Phillips screwdriver into the hole in the CPU cooler fans and unscrew the clamp.  Remove the clamp and discard it.

### Identify hot and cold sides of TEC

Briefly connect the TEC Peltier unit to a power supply and find out which side gets cold.  Label it or remember.  Mine has text printed on the cold side.

### Install ESPHome configuration

Before installing the XIAO into the FBD, install the ESPHome configuration and attach it to your Wi-Fi.  This guide doesn't cover ESPHome installation; see [the ESPHome documentation](https://esphome.io/) for info.

Verify that you can access the ESP32's web server now.


## Building the PCB Assembly

### Solder Components

Solder the components onto the PCB in this order.

 1. Male Headers.  You can use a breadboard to align most of the male headers while you solder them.
 2. Resistors
 3. QWIIC connector (optional)
 4. Female headers
 5. 5V regulator (MP1584)
 6. Terminal block
 7. Barrel jack
 8. Power MOSFET

### Set Voltage

Before attaching the XIAO, attach the 12V power supply and adjust the MP1584 regulator to 5 volts.

### Install XIAO

Plug the XIAO board in to the female headers.  Note that you should not attach the USB while the XIAO is in place.  For configuration updates, either use Wi-Fi or remove the XIAO before attaching USB.

## Assembly

This section shows the steps to assemble the parts.

### Insert M5 nuts

Insert the M5 nylon lock nuts into the housing halves.  Put an M5 screw through the hole, screw the nut onto it, and pull it back out until the nut is seated flush.

Note: the nuts are held in by friction.  Be careful not to dislodge them from here on.

### Insert NH-U9S into Housing Left Half

It will fit.  It has to be aligned just so, then it drops in.

### Insert fan into Housing Left Half

Orient the fan so the it blows air into the fins, and the cable is at the position shown.

### Affix TEC

Orient the TEC Peltier unit so that its hot side is against the CPU block and its wires fit into the slots in the Housing Left Half.  Apply enough thermal paste to make a thin layer over the whole mating surface and press it into place.
 
### Push Housing Right Half On

Feed the fan wire through the tunnel in the Housing Right Half.  Be careful not to pinch the wire, and lower the right half onto the assemblied parts.  It will fit.  When it does, it will drop on.  It may be slightly open at the back (1mm or less), that's okay.

### Screw the housing halves together

Use five M3x16 screws.  You should be able to pull the housing halves together to close any gap between them.  If not, something is probably pinched inside.  Open it up and correct the problem.

### Attach the Bottom Vent Slider

Put the Bottom Vent Slider in diagonally, then rotate it into position.

The vent slider is adjustable.  Start with it covering about half of the fan.

### Affix the heatsink and temperature probe

Push the temperature probe all the way into the heatsink so that it is contacting the heatsink base.  Orient the heatsink so that the fins are horizontal and the probe is slightly above center.  Apply thermal paste and stick it on.

### Attach the Housing Front

Feed the four wires through the holes in the Housing Front.  Push the Housing Front against the rest of the assembly.  Verify that the temperature probe lines up with its hole.

**Carefully** insert the M3x30 screws into the big holes and engage the nuts.  Do not push the nuts out of place.  Screw the screws down but not tight yet.

Insert four M3x30 screws into the four small holes and tighten them.  Then go back and tighten the M5 screws until the gap between the Housing Front and the Housing Left/Right Half is closed.

The M5 screws press the heatsink, TEC, and CPU cooler together to ensure a good thermal bond.

### Seal the temperature probe hole

Put the two Half Seals in and screw them down with four M3x8 screws.

Note.  The probe should stick out about as far as shown.  If it's more, then the probe may not be against the heatsink base.

### Install PCB, DHT22, and standoffs

Fit the PCB and the DHT22 into their standoffs.  Note the orientation of the PCB on its standoff.  Attach the PCB with two M3x10 screws, and attach the DHT22 with two M2.5x10 screws.

### Connect TEC wires

Cut the wires to length.  Install a ferrule on each wire.  Screw the ferrules into the terminal block on the PCB, and mind the polarity.

Note that the holes in the Housing Front are big enough to pass the ferrules through if you need to disassemble the dehumidifier.

### Connect temperature probe wires

Cut the wires on the DS18B20 temperature probe to length.  Crimp on 3 female Dupont pins and a connector.  Note the pinout as shown in the schematic or back side of the PCB.  Plug it into the PCB.

### Connect fan wires

The fan already has a compatible connector.  Note that Pin 1 on the connector is Pin 4 on the PCB.  Check the pinout.

### Connect DHT22 wires

Use the female-to-female cable to attach the DHT22 to the PCB.  Note the pinout.

### Attach the Electronics Cover

No, really.  Leave the Electronics Cover off for now.  You'll need access.  Just verify that it fits.  You'll have to mash things together; don't pinch the antenna or any wires.  Secure the cover with two M3x40 screws.

### Attach the drain tube

Spread some silicone caulk around the tip of the drain tube, then insert it into the drain hole.  Let it set according to the caulk instructions.

### Test

Dunno.  Mine worked on the first try, because I'd tested everything on a breadboard.  Attach power, look for smoke, listen for the fan, put your finger on the heatsink and see whether it's getting cold.  Connect to the ESP32's web server and see whether the sensor values look sane.  Try turning it off and on from the web interface.  Debug as needed.
