Spark Core energyShield Library
============

This is the Spark Core adaptation library for the NightShade Electronics energyShield. It allows Spark.io users to easily access some of the energyShield's fuel gauge functionality. It uses the Arduino Wire Library to communicate the the fuel gauge and the calculates current battery information.

energyShield repo: https://github.com/nightshade-electronics/energyShield

energyShield site: http://www.ns-electric.com/products/energyshield/

Copyright (c) 2014, NightShade Electronics. Written by Aaron Liebold for NightShade Electronics. Revised BSD license.



This Library implements the following commands.

NS_energyShield <object>

	Function: Defines NS_energyShield object <object>
	Returns: nothing
	
<object>.address()

	Function: Changes the target address used by the library
	Returns: nothing
	
<object>.voltage()

	Function: Reads the battery voltage from the fuel gauge
	Returns: [int] Voltage in mV
	
<object>.current()

	Funtion: Reads current charging (positive) or discharging (negative) the battery
	Returns: [int] Current in mA
	
<object>.percent()

	Function: Reads the percent of charge remaining in the battery
	Returns: [int] Percent of charge in 0.5% increments (2 * Percent Charge)
	
<object>.temperature()

	Function: Reads the temperature from the fuel gauge
	Returns: [int] Temperature in 0.125 oC increments (8 * Temperature)


To make this library compatible with the Spark library format, the following steps were performed:

* Moved /examples/ folder up to root directory
* added files: LICENSE, spark.json
* renamed `NS_energyShield.*` to `nightshade-energyshield.*`
* .cpp: removed `Arduino.h` includes
* .cpp: relinked `nightshade-energyshield.h` in `nightshade-energyshield.cpp`
* .ino: updated setup() `!Serial` wait loop to Spark-compatible format
* .cpp: moved `Wire.begin()` from object instantiation to `void setup()`
* .cpp: changed binary address variable to `0b` Spark format
