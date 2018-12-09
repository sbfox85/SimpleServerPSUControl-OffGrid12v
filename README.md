# SimpleServerPSUControl-OffGrid12v
Simple control of multiple server switch mode PSU's to feed 12v-230v inverter to run high load sensitive electronics from a standard generator

This is a simple controller which, using MQTT, will ensure that parallel (upto 4) server PSU's are controlled correctly to allow them to be run from a dirty output generator. They will feed a 12v lead acid traction bank, which will in turn feed the 12v-230v inverter.

In an ideal system, this would use the PSU's in series, to offer 48v, however I am working with what I have (a decent pure sine wave, low frequency 3kw 12v-230v Inverter and a 6cell 940ah FLA Traction Battery).

The main purpose is to allow me to charge my EV, a Renault Zoe with generator power if I need to. However it can also be used to allow hybrid charging, using the grid and off grid solar. My 1.8kw solar bank is vehicle mounted, and therefore can't be hard wired. This setup wouldn't be allowed to grid-tie in the UK, as it must be hard wired. This is a work around for me.

The Zoe will charge at any current (when on single phase, 3 phase requires 8amp+) between 6amp and 32amp. The efficiency is rather low at 6amp, so the aim of the setup is to charge at as higher output as possible, limited by the 3kw inverter. At 230v this means 13amp. In reality, I will aim for 12amp to be the limit, to allow some headroom.

Server PSU Control:
- Control Contactor to PSU's.
- Monitor each PSU's Status (ie outputting, or fault)
- Monitor the Combined DC Current flow from PSU's
- Monitor the generators frequency and voltage, cutting the PSU's power if it goes out of specification, and signal "emergency stop" if required.
- Allow hybrid mode, when PSU's are grid-fed.
