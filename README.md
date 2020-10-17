# TagConnect
## TC2030-MCP and TC2050-CTX adapters for different boards.
![alt text](https://pbs.twimg.com/profile_images/1625182695/Tag-Connector_with_legs.jpg)
TagConnect (www.tag-connect.com) cables are *very nice*, but *pretty expensive* for hobbyists.
Due to I am dealing with a big variety of microcontrollers, I bought 10-pin cable for ARM Cortex (TC2050-CTX), and 6-pin cable for Microchip ICD (TC2030-MCP), and then I am doing the adapters for other MCUs.
_Actually, I bought TC2030-MCP-NL afterwards, but it is pretty much the same, NL stands for NoLegs, so it is good for flashing, and not that much for development and debugging. I am dealing with all listed activities, so I need it_

If someone is interested to buy a pcb, or an adapter, you can contact me here, I never order a single PCB, and usually I do have spare.
I can ship it inside EU any time, and occasionally to UA.
This is how tc2030, tc2030-nl, tc2050 and tc2050-nl footprints looks like on PCB:
![alt text](http://www.thingamafob.com/wp-content/uploads/2012/12/IMG_7106-1024x682.jpg)
-----
# mcp2jlink
TC2030-MCP to Segger JTag, target is ARM Cortex-M (SWD interface), tested on stm32f0, stm32f1xx, stm32f4xx, stm32f7xx.
Just an adapter, 2 connectors on the PCB.
### parts:
- RJ12 connector, I took from Farnel, part no 1654815
- https://www.aliexpress.com/item/32890057619.html - 2x10 JTag Header, but I am not happy with it does not really looks like original one.
#### Pinout:
The pinout seems to be original, but I've never tested neither my boards with original cable, nor original boards with my cable (definitely works fine with my adapter and my pcb boards).
| Pin | Signal | MCP2030 signal  |
|:-:| - | - |
| 1 | SWD_OUTPUT | MCLR |
| 2 | GND | Vcc |
| 3 | SWD_CLK | Vss |
| 4 | nRST (nRESET) | PgD |
| 5 | SWD_IO | PgC |
| 6 | N/C | PgM/NC |
_I am not SWDO (pin #1) in my designs, the trace output works better and faster with RTT through SWD_CLK/SWD_IO pins_
#### Revision history:
- Rev A - failure, deleted.
- Rev B - working version, PCBs are ready and tested.
- Rev C - thermal settings for copper pouring is changed, will be ordered occasionally.
-----
# mcp2pickit
TC2030-MCP to PICKit, targets are Microchip's pic1x, pic24, pic32 - any serie that suppose to work PICKit.
Just an adapter, 2 connectors and PCB.
### parts:
- RJ12 connector, I took from Farnel, part no 1654815
- any 90-angle male 6x1 header (or 5x1 - for most of MCUs you can skip 6th pin) with step of 2.54mm
#### Pinout is 1:1, so it is basically 
| Pin | Signal | MCP2030 signal  |
|:-:| - | - |
| 1 | MCLR | MCLR |
| 2 | Vcc | Vcc |
| 3 | Vss | Vss |
| 4 | PgD | PgD |
| 5 | PgC | PgC |
| 6 | PgM/NC | PgM/NC |
#### Revision history:
- Rev A - ready, will be ordered occasionally (never tested yet)
-----
# mcp2esp32
USB to UART converter (CP2102 based), 1A 3v3 power source to power up the Esp32 board, and RTS+DTR for EN and Boot0/IO0 control - same as original DevKits are using. No commercial programmer is needed.
The EN and Boot0 should be pulled up to 3v3 through resistor of 10k.
MCP-NL to ESP32 (in my case - ESP32-Wroom-32 module, should work fine on any ESP32 based module).
### parts:
- RJ12 connector, I took from Farnel, part no 1654815
- micro-USB type B connector, SMD, I took part no "207A-BBA0-R" from "ATTEND TECHNOLOGY", part number "2442736" in Farnel looks pretty much the same.
- CP2102, QFN-28
- LDO, I took MCP1826S in sot223 due to availability, power (1A at least) and convenient pinout.
- transistor sot23, bc817 - 2 pcs
- capacitor 0603, 100nF - 3 pcs
- capacitor 0805, 1uF - 2pcs
- capacitor 0805, 4,7uF - 2 pcs
- resistor 0805, 10k - 4 pcs _(not sure if I will take 2 x 10k, 2 x 4k7 instead)_
#### Pinout: no original one, so I did it this way:
| Pin | Signal | MCP2030 signal  |
|:-:| - | - |
| 1 | EN | MCLR |
| 2 | Vcc (3v3 1A from PCB) | Vcc |
| 3 | GND | Vss |
| 4 | PC-TxD -> ESP32-Rx | PgD |
| 5 | PC-RxD <- ESP32-Tx | PgC |
| 6 | Boot0/IO0 | PgM/NC |
#### Revision history:
- Rev A - ready, will be ordered occasionally (never tested yet)
- next step - add ESD protection to USB.
-----
# mcp2r16c
**(Not yet designed)**
Renesas R5F21xxxx series, no original cable, to pinout is an open question.
-----
# ctx2msp430
**(Not yet designed)**
The original cable is TC2050 only, so here comes the Cortex (ARM) adapter at last.
