# TagConnect
TC2030-MCP and TC2050-CTX adapters for different boards.

TagConnect (www.tag-connect.com) cables are very nice, but pretty expensive for hobbyists.
Due to I am dealing with a big variety of microcontrollers, I bought 10-pin cable for ARM Cortex (TC2050-CTX), and 6-pin cable for Microchip ICD (TC2030-MCP), and then I am doing the adapters for other MCUs.

If someone is interested to buy a pcb, or an adapter, you can contact me here, from time to time I have some spare.
I can ship it inside EU any time, and occasionally to UA.

The pin numbers are (if you will look at the PCB side):
   x
  1 2
  3 4
  5 6
 x   x

-----

#Part list:

1. mcp2jlink.
Just an adapter, 2 connectors on the PCB.
- RJ12 connector, I took from Farnel, part no 1654815
- https://www.aliexpress.com/item/32890057619.html - 2x10 JTag Header, but I am not happy with it - does not really looks like original one.
The pinout seems to be original, but I've never tested neither my boards with original cable, nor original boards with my cable (definitely works fine with my adapter and my pcb boards).
1 - SWD_OUTPUT              - @MCLR   / I am not using one, the trace output works better and faster with RTT through SWD_CLK/SWD_IO /
2 - GND                     - @Vcc
3 - SWD_CLK                 - @Vss
4 - nRST (nRESET)           - @PgD
5 - SWD_IO                  - @PgC
6 - N/C                     - @PgM/NC

2. mcp2pickit
Just an adapter, 2 connectors and PCB.
- RJ12 connector, I took from Farnel, part no 1654815
- any 90-angle male 6x1 header (or 5x1 - for most of MCUs you can skip 6th pin) with step of 2.54mm
The pinout is 1:1, so it is basically 
1 - MCLR       - @MCLR
2 - Vcc        - @Vcc
3 - Vss (GND)  - @Vss
4 - PgD        - @PgD
5 - PgC        - @PgC
6 - PgM/NC     - @PgM/NC

3. mcp2esp32
USB to UART converter, 1A 3v3 power source, and RTS+DTR for EN and Boot0/IO0 control - same as original DevKit are using. No commercial programmer is needed.
The EN and Boot0 should be pulled up to 3v3 through resistor of 10k.
- RJ12 connector, I took from Farnel, part no 1654815
- micro-USB type B connector, SMD, I took part no "207A-BBA0-R" from "ATTEND TECHNOLOGY", part number "2442736" in Farnel looks pretty much the same.
- CP2102, QFN-28
- capacitor 0603, 100nF - 3 pcs
- capacitor 0805, 1uF - 2pcs
- capacitor 0805, 4,7uF - 2 pcs
- resistor 0805, 10k - 4 pcs <<< not sure if I will take 2x10k, 2x4k7 instead
- transistor sot32-3, bc817 - 2 pcs
As far as there's no original cables, the pinout I took is:
1 - EN                     - @MCLR
2 - Vcc (3v3 1A from PCB)  - @Vcc
3 - GND                    - @Vss
4 - PC-TxD -> ESP32-Rx     - @PgD
5 - PC-RxD <- ESP32-Tx     - @PgC
6 - Boot0                  - @PgM/NC

4. ctx2msp430
The original cable is TC2050 only, so here comes the Cortex (ARM) adapter at last.
(Not yet designed)

#Revision History

1. mcp2jlink.
TC2030-MCP to Segger JTag, target is ARM Cortex-M (SWD interface), tested on stm32f0, stm32f1xx, stm32f4xx, stm32f7xx.
-----
Rev A - total mess, does not worth of seeing.
Rev B - working version, PCBs are ready and tested.
Rev C - thermal settings for copper pouring is changed, will be ordered occasionally.

2. mcp2pickit.
-----
TC2030-MCP to PICKit, targets are Microchip's pic1x, pic24, pic32 - any serie that suppose to work PICKit.
Rev A - should work, will be ordered occasionally.

3. mcp2esp32
-----
MCP-NL to ESP32 (in my case - ESP32-Wroom-32 module, should work fine on any ESP32 based module).

Rev A - ready, will be ordered soon.


4. ctx2msp430
-----
(not yet designed)