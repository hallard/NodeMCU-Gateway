NodeMCU ESP8266 Gateway
=======================

The gateway can host several funny things like

- Socket to plug a NodeMCU V1.0
- Pins to connect I2C or SPI OLED 128x64
- Pins to connect 2.2" or 1.8" TFT LCD
- RFM69 or RFM12B on board module
- RFM69, RFM12B or NRF24L01 on board module (on NRF version)
- RFM92, RFM95, RFM96, RFM98, RFMH69, RFMHW69 or RFMHCW69 on board module (on LORA version)
- Lipo Battery connector for testing and move the Gateway (no charger on board)
- 3V3 On board regulator is provided by NodeMCU Board
- Data connection for any cheap ebay ASK RX receiver
- 2 x grove I2C connector to connect other I2C devices
- 2 onboard nice WS2812 RGB LED
- Footprint for Atmel ATSHA204 (I2C version due to lack of I/O)
- Created a version with NRF24L01 connector instead of a grove I2C (end of this page)

This page has been updated to reflect the GPIO changes and the PCB also, it's now V1.2.

NRF24L01 version are now tested thanks to [mannkind][6]. As suggested NRF version 1.2 has how been corrected to have NRF24L01 wiring same has mysensors configuration and added place for capacitor near NRF24L01.

LORA boards are **Not tested yes use at your own risk**


New Version 1.2 boards
======================
New boards version V1.2 these boards add a MOSFET transistor to protect againns reversed power supply. Trust me this will avoid you to burn some nodeMCU board (but nobody plug reversed powed, never ?)

New board, supporing LORA modules

Version 1.1 boards
==================
Boards V1.1 are tested ok (RFM69), no problem at all, just SILK error on TFT connector, TFT pin 4 is RST or VIN (depending on solder pad) not GPIO0, also R3 10K is not needed since GPIO2 is already pulled up by 12K on nodeMCU boards.

SILK problem solved in V1.1a+, I also put VIN/RST solder pad bigger for easier soldering.

This is a bunch of V1.1 white PCB boards, nice ?

<img src="https://raw.githubusercontent.com/hallard/NodeMCU-Gateway/master/pictures/V1.1-White-Boards.jpg">

Version 1.1 boards
==================
Boards V1.0 worked but I needed a fix for RMF69 pin connection to ESP826 GPIO, let me explain :    
ESP8266 to boot correctly needs some pins at defined level, GPIO15 must be LOW and GPIO2 must be HIGH. Unfortunatlly with RFM69 connected as IRQ to GPIO2 and SS to GPIO15 it does not boot because RF69 pull it DIO IRQ to LOW, making GPIO2 LOW and ESP8266 not booting. The fix is to reverse the wiring, connect IRQ to GPIO15 and SS to GPIO2 (and do according changes in the code).


Detailed Description
====================

No specific documentation for now, but very close in term of feature to Particle Gateway I created and blogged on this dedicated [post][1]

### Schematic (Classic version)
![schematic](https://raw.githubusercontent.com/hallard/NodeMCU-Gateway/master/pictures/NodeMCU-Gateway-sch.png)  

### Boards (Classic version)
<img src="https://raw.githubusercontent.com/hallard/NodeMCU-Gateway/master/pictures/NodeMCU-Gateway-top.png" alt="Top" width="60%" height="60%">    

<img src="https://raw.githubusercontent.com/hallard/NodeMCU-Gateway/master/pictures/NodeMCU-Gateway-bottom.png" alt="Bottom" width="60%" height="60%">     

You can order the PCB of this board at [OSHPARK][3] (V1.2)

### Assembled boards

*V1.0 tested and assembled boards*    

<img src="https://raw.githubusercontent.com/hallard/NodeMCU-Gateway/master/pictures/NodeMCU-Gateway-Top.jpg" alt="Top" width="75%" height="75%">    

<img src="https://raw.githubusercontent.com/hallard/NodeMCU-Gateway/master/pictures/NodeMCU-Gateway-Bottom.jpg" alt="Bottom" width="75%" height="75%">     

With a nice 1.3" Oled display    
<img src="https://raw.githubusercontent.com/hallard/NodeMCU-Gateway/master/pictures/NodeMCU-Gateway-OLED.jpg" alt="OLED" width="75%" height="75%">    

### Schematic (NRF24L01 version)
![schematic](https://raw.githubusercontent.com/hallard/NodeMCU-Gateway/master/pictures/NodeMCU-Gateway-NRF-sch.png)  

### Boards (NRF24L01 version)
<img src="https://raw.githubusercontent.com/hallard/NodeMCU-Gateway/master/pictures/NodeMCU-Gateway-NRF-top.png" alt="Top" width="60%" height="60%">    

<img src="https://raw.githubusercontent.com/hallard/NodeMCU-Gateway/master/pictures/NodeMCU-Gateway-NRF-bottom.png" alt="Bottom" width="60%" height="60%">     

You can order the PCB of this board at [OSHPARK][4] (V1.2)

### Schematic (LORA version)
![schematic](https://raw.githubusercontent.com/hallard/NodeMCU-Gateway/master/pictures/NodeMCU-Lora-Gateway-sch.png)  

### Boards (LORA version)
<img src="https://raw.githubusercontent.com/hallard/NodeMCU-Gateway/master/pictures/NodeMCU-Lora-Gateway-top.png" alt="Top" width="60%" height="60%">    

<img src="https://raw.githubusercontent.com/hallard/NodeMCU-Gateway/master/pictures/NodeMCU-Lora-Gateway-bottom.png" alt="Bottom" width="60%" height="60%">     

You can order the PCB of this board at [OSHPARK][5] (V1.2)



##License

You can do whatever you like with this design.

##Misc
See news and other projects on my [blog][2] 
 
[1]: https://hallard.me/particle-gateway/
[2]: https://hallard.me
[3]: https://oshpark.com/shared_projects/vwEm8gUg
[4]: https://oshpark.com/shared_projects/3wE3bYYY
[5]: https://oshpark.com/shared_projects/HIb6K9BL
[6]: https://github.com/hallard/NodeMCU-Gateway/issues/1