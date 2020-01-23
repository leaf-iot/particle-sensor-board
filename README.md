# particle-sensor-board
Particle / Feather based sensor interface board

Interface for Particle Boron/Argon/Xenon and other Feather compliant boards.

Features:
- Input voltage and current monitoring via INA226
- On-board microSD card slot for data logging
- On-board BME280 Sensor for Temp / Humidity / Barometric Pressure
- Two Atlas Scientific EZO sensor interfaces with full isolation
- Two 4-20mA current loop interfaces
- 3.3V, GND, A0, A1, D8 pins exposed on screw terminal block
- DC input is 3.5x1.1mm (meant for Voltaic Systems solar panels)
- Enable / Disable EZO and 4-20mA power via I/O pins from Feather device
- TTL Serial pins exposed via separate 4-pin header

Known Issues:
- There is a bug in the microSD card circuit, the MISO and MOSI lines were reversed accidentally during development. Due to this, software SPI needs to be used with the pins configured this way.
- No on-board battery battery charging circuit. We relied on the Particle Boron's built in BQ24195 chip for charging, however up to this point we have had nothing but issues with this. There have been several hardware and firmware issues identified by the community with the Boron (including incorrectly limiting charge current when using the VUSB pin, input current limit settings not being honored, as well as several issues with solar charging in sleep mode. Some of these problems are yet to be fixed as of this release. 
- Particle Boron u-blox modems are capable of connecting to Verizon, but Boron's produced after a certain date were never registered with Verizon, and as such you will have nothing but problems with connectivity and FPLMN blacklists if you attempt to use these devices with Verizon or Hologram sim cards. Stick with the internal SIM and you should be okay.
