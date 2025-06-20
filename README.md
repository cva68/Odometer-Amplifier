# Motorcycle Odometer Amplifier

Interface between a digital vehicle speed / odometer sensor and a motorcycle dashboard, which operate on different logic levels.

The dashboard and sensor are part of a Chinese clone of a Honda CBR250RR, making finding suitable replacement components difficult. A past owner replaced the vehicle speed sensor with an incompatible component. The replacement sensor, when provided with 5V, outputs 600mVp-p square wave on the signal line. The dashboard expects 5Vp-p, and has its signal line pulled up to 5V by default - the sensor seems incapable of pulling this down to logic low.

Using a Schmitt trigger implemented with an LM358 op-amp, the 600mVp-p signal is amplified to ~3.5Vp-p. This voltage now exceeds the threshold required to drive an NPN transistor, which is used to pull the signal line of the dashboard down.

The dashboard provides a "regulated" 5V for these components, but with ~400mVp-p ripple. A Zener diode was added to clamp over-voltage, and a LC low-pass filter was included. This proved adequate for reliable operation of the Schmitt trigger.

![Schematic](schema.jpg)

The design was implemented on strip-board, had larger components secured with hot glue to prevent vibration damage, and installed in a off-the-shelf plastic enclosure on the bike.

![Strip board](stripboard.jpg)
