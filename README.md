# ESPblaster

![PCB Preview](https://github.com/sammy0025/ESPblaster/raw/master/Graphical%20Assets/Preview.png)

Designed by [FourierIndustries](https://fourier.industries) by Pan Ziyue

## Overview
The ESPblaster is a simple and straightforward ESP8266-01 flashing device, with onboard logic level translation, high stability voltage regulation, and an active-low DIP switch to toggle the ESP8266-01 module's startup states. All of the components are either through-hole or 1206 SMD, which makes the board easily solderable. JP1, JP2 and JP3 are jumpers on the board that should be closed by default with a solder blob. This circuit board provides a quick and easy alternative to flashing or interacting with the ESP8266-01 module without complicated breadboarding. 

## Interface
The ESPblaster has a 6-pin serial interface:

* **DTR** (not wired to anything)
* **TXO** (Transmit Out) [5V compliant]
* **RXI** (Receive In) [5V compliant]
* **VCC** (5V in)
* **GND**
* **RX3** (Receive In) [3.3V compliant]

## DIP switches
The ESPblaster packs a DIP switch to alter the startup states, as well as reset the module or disable the module. 

#### Warning: the DIP switch is an active low switch! This means that flipping the switch up to "On" will pull low the circuit!

The DIP switches are responsible for the following states (from left to right, from the front face of the board):

1. **CH_PD** (Chip Enable)
2. **RST** (Reset)
3. **GPIO0**
4. **GPIO2**

## Startup states table

|                  | CH_PD | RST | GPIO0 | GPIO2 |
|------------------|:-----:|:---:|:-----:|:-----:|
| Normal Startup   |   1   |  1  |   1   |   1   |
| Flash bootloader |   1   |  1  |   0   |   1   |
| Reset            |   1   |  0  |   X   |   X   |
| Disable          |   0   |  X  |   X   |   X   |

## Solder blob jumpers
JP1, JP2 and JP3 are solder blob jumpers, which should be closed by default. They are responsible for the following:

* **JP1**: Connects GPIO0 to the DIP switch
* **JP2**: Connects GPIO2 to the DIP switch
* **JP3**: When connected, the RXI signal will pass through the logic level shifter and if disconnected, you must use the RX3 pin to supply 3.3V logic for the RX of the ESP8266-01.