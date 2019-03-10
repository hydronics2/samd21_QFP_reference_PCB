# samd21_QFP_reference_PCB

This is a reference design for a SAMD21 for easy SWD programming and testing.  This layout should work with any SAMD21 QFP package. The QFP package is pretty easy to solder and gives you about the same amount of pins as the original Aruduino 328P. The following SAMD21 packages are QFP:
- SAMD21E15 32kB of Flash **(read this)
- SAMD21E16 64kB of flash **(read this)
- SAMD21E17 128kB of flash
- SAMD21E18 256kB of flash

![](https://github.com/hydronics2/samd21_QFP_reference_PCB/blob/master/PCB_top.png)

I wanted to start to try SWD programming and these are the less expensive version of the popular SAMD21G on Adafruit and Sparkfun boards.
This PCB design relies heavily on Adafruit and Sparkfun reference design. I realized Adafruit has a similar design for their [32pin Trinket](https://learn.adafruit.com/assets/45723). They do not have a 32.768 crystal or a ferrite bead as recommended by Atmel. Not sure why/how that works. Instead of running the two pins PA00/PA01 to a crystal, they run them to their Dotstar LED!

You can order boards from Oshpark using this link: [project](https://oshpark.com/shared_projects/EjZP7lWQ)

Here's a list of parts:


- ATSAMD21E15B from [digikey](https://www.digikey.com/product-detail/en/microchip-technology/ATSAMD21E15B-AFT/1611-ATSAMD21E15B-AFTCT-ND/6832773). Don't get the ATSAMD21E15L!... the pinout is slightly different.
- 10 pin SWD Header from [digikey](https://www.digikey.com/product-detail/en/microchip-technology/ATSAMD21E15L-AFT/1611-ATSAMD21E15L-AFTCT-ND/6832779)
- generic 5.08mm pitch screw headers (or 5mm)
- 	FIXED IND 10UH 500MA 300 MOHM [digikey](https://www.digikey.com/product-detail/en/tdk-corporation/MLZ2012N100LT000/445-6762-1-ND/2523583)
- 3.3V Regulator (18V max input) [mouser](https://www.mouser.com/ProductDetail/511-LDL1117S50R)
- T0-252-3 Mosfet (not needed) [mouser](https://www.mouser.com/ProductDetail/ON-Semiconductor-Fairchild/FDD8780?qs=%2fha2pyFadugI30EyIBTPkO8PumBRFL59Ls98N48NSzc%3d)
- USB micro connector [digikey](https://www.digikey.com/product-detail/en/amphenol-icc-fci/10118194-0001LF/609-4618-1-ND/2785382)
- standard 6mmx6mm tactile button [sparkfun](https://www.sparkfun.com/products/97)
- screw terminal 5mm pitch [sparkfun](https://www.sparkfun.com/products/8432) or [aliexpress](https://www.aliexpress.com/wholesale?catId=0&initiative_id=SB_20190221221755&SearchText=pcb+screw+terminal)
- input protection diodes on the 12V and USB input into the regulator. This is Adafruit's design. [digikey](https://www.digikey.com/product-detail/en/diodes-incorporated/B130-13-F/B130-FDICT-ND/815318)
- 32.768khz crystal (if needed, see above trinket design) [digikey](https://www.digikey.com/product-detail/en/epson/FC-135-32.7680KA-AG3/SER4086DKR-ND/6132726)
- crystal capacitors C7/C8 based on a 7pf load from the above crystal and assumed 2pf stray capacitence, CX1 = CX2 = 2(7pF - 2pF) = 10pF [digikey](https://www.digikey.com/product-detail/en/wurth-electronics-inc/885012006051/732-7793-1-ND/5454420)


SWD Programmer/Debugger: [Segger](https://www.digikey.com/product-detail/en/segger-microcontroller-systems/8.08.91-J-LINK-EDU-MINI/899-1061-ND/7387472)

![schematic](https://github.com/hydronics2/samd21_QFP_reference_PCB/blob/master/schematic.JPG)

Notes:
- add a ground plane
- chagne the silkscreen to SAMD21E15
- change the silkscreen C7/C8 from 15pf to 10pf




**READ THIS
The SAMD21E15 only has 32kb of flash. Fine for 8bit architecture but not for 32bit SAMD21 architecture!!
About 50 lines of simple code uses 332 bytes (12%) in for the UNO but compiles over 9,000 bytes (9248 bytes (56%)) for the SAMD21E15, SAMD21E16, SAMD21E17, etc

That means that I should have gone with the SAMD21E17 or SAMD21E18 with 128 or 256kb respectively.

