# ember mug 2

* product page https://ember.com/products/ember-mug-2?variant=30843977760853
* FCC certification https://fccid.io/2AILTCM17
  * internal photos https://fccid.io/2AILTCM17/Internal-Photos/Internal-Photos-3517267
    * doesn't show the heating element, unfortunately
  * I think this is for not the most recent revision, though?
  * [this](https://fccid.io/2AILTCM21) might be the right version, but internal photos aren't available until 2022-05-16


here's a teardown by JerryRigEverything of a different ember model
https://www.youtube.com/watch?v=qeWvgZLz9yU


# teardown/analysis
https://twitter.com/madewithlinux/status/1464794918300360708


## heating element/temperature sensor cable
* it's 8 pins
* has a sticker on it with a data matrix code that reads EM1001151A09110WY3
  * the same code is printed in text around the edge of the sticker, EM1001151A 09110WY3
  * this doesn't bring up anything in google
* the cable itself is two layered and has vias and stuff going between the layers
  * is it actually a flex PCB?
* the traces for the 3 heating element pins and ground are the largest
  * the heating element makes sense
  * but why is the ground trace so thick? it doesn't seem to be involved in heating at all...


## heating elements
it appears to have two heating elements
* 12 ohm, connected to heater_charger test point on PCB
* 2 ohm, connected to heater_bat test point on PCB

the common pin is next to the ground pin on the heater connector, but I have yet to find where it's connected to on the PCB.
The ground pin on the connector doesn't seem to be connected to either heater, so I'm guessing it's used by the temperature sensor


## temperature sensor
there's 6 pins left on the heater connector, and none of them seem to be short to each other or any other connector pin (including ground).

temperature sensor says T275 on it, which looks like a TI TMP275 based on datasheet search.
datasheet link: https://www.ti.com/lit/ds/sbos363f/sbos363f.pdf?ts=1638144493202
(The part where it says "Industry Standard LM75 Form Factor and Pinout" is a very good sign lol)

arduino library: https://github.com/jeremycole/Temperature_LM75_Derived
* https://www.arduino.cc/reference/en/libraries/i2c-temperature-sensors-derived-from-the-lm75/
* https://platformio.org/lib/show/2860/I2C%20Temperature%20Sensors%20derived%20from%20the%20LM75
* This specific sensor is supported https://github.com/jeremycole/Temperature_LM75_Derived/blob/master/doc/Sensors.md
* 


It looks like there's also two other little components stuffed in the side of the inside of the mug.
not sure what they are, but it seems like they're intentionally right next to the inside wall, and packed in foam, so I'd think temperature sensors of some kind? but they're really small, so idk.


# alternatives that look interesting
https://www.amazon.com/nicelucky-Cooler-Coffee-Warmer-Desktop-2IN1/dp/B07TPF7M3N

