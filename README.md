Adafruit-PCD8544-Nokia-5110-LCD-library-for-Spark
=================================================

Nokia 5110 LCD library adapted for Spark Core by Paul Kourany, April 2014

!!! Updated for Libraries 2.0, Jan 2017

This code compiles on the Particle web IDE

Requirement
-----------

This library uses the Adafruit_GFX library.


Usage
-----
To use HARDWARE SPI, connect the display as follows for the demo program to run:

Spark       Nokia 5110
A5 (MOSI)     DIN
A4 (MISO)      -
A3 (SCK)      CLK
A2 (SS)       CS
D3            RST
D2            D/C
GND           GND
3V3           VCC

D3(RST) and D2(D/C) may be any pin but changes must be made to constructor line:

```
	Adafruit_PCD8544(CS, DC, RST);

	demo eg: Adafruit_PCD8544 display = Adafruit_PCD8544(SS, D2, D3);
```

To use SOFTWARE SPI, connect the display as follows, the SCLK, DIN, DC, CS and RST lines must
be specifiec and connected to the display and the constructor called as follows:

```
	Adafruit_PCD8544(SCLK, DIN, DC, CS, RST);

	eg: Adafruit_PCD8544 display = Adafruit_PCD8544(A3, A5, D2, A2, D3);
```

NOTES:
- Modified for Particle Photon compatibility with Core backwards compatibility
- Modified code for Spark Core compatibility
- Added hardware and (fast) software SPI to fastSPIwrite()
- Added new create object methods for HardwareSPI:

  Adafruit_PCD8544 display = Adafruit_PCD8544(CS, DC, RST);
    - Specify hardware SPI, chip select(CS pin), DC (data/command pin) and RST (reset pin)

  Adafruit_PCD8544 display = Adafruit_PCD8544(DC, RST);
    - Specify hardware SPI, NO chip select, DC (data/command pin) and RST (reset pin)

- Existing create methods will use (fast) software SPI code
- The existing slowSPIwrite() function which uses shiftOut() is not used anywhere in the library

