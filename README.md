# STS1 RF Module

This PCB is the RF subsystem of the STS1 COBC ("Communication and On Board Computer") isolated on a separate PCB to test the RF subsystem.  
The complete RF path was simulated using QUCS (see [the STS1_RF_Simulations repo](https://github.com/SpaceTeam/STS1_RF_Simulations) for the files).

It is based around the Si4463 RF IC and features an LNA, 2W power amplifier and filtering built for our CubeSat and is designed for a frequency aroudn 435MHz.

Feel free to use this for whatever you want but there are two important things to consider:
- 2W is way more than legal without some form of license in most countries so make sure that whatever you are planning to do is legal in your country.
- The filtering and matching is designed for 435MHz. For any other frequency you'll probably go into the QUCS project and find suitable values for your frequency.
  - The matching of the Si4463 is described in [AN643](https://www.silabs.com/documents/public/application-notes/AN643.pdf) and [AN648](https://www.silabs.com/documents/public/application-notes/AN648.pdf)
  - The matching of the PA and LNA is done using the [QUCS matching network calculation tool](https://qucs-help.readthedocs.io/en/0.0.19/matching.html)
  - The low pass filters most likely can stay the same if you don't drastically change the frequency
  - The band pass filters are stolen from [ORESAT0 C3](https://github.com/oresat/oresat-c3/) so you'll have to figure this out on your own :P
- When using this in space, you'll want to add some form of watchdog to the `TX_Block` input and latch-up protection for at least the 3.3V rail (the power amplifier has it's own e-fuse on the 5V rail)

## Current state

### v1.0

Currently untested!  
The TX path excluding the RF switch were mostly tested before but the rest is untested.  
