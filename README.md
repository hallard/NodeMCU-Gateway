NodeMCU ESP8266 Gateway
=======================

The gateway can host several funny things like

- Socket to plug a NodeMCU V1.0
- Pins to connect I2C or SPI OLED 128x64
- Pins to connect 2.2" or 1.8" TFT LCD
- RFM69 or RFM12B on board module
- Lipo Battery connector for testing and move the Gateway (no charger on board)
- 3V3 On board regulator is provided by NodeMCU Board
- Data connection for any cheap ebay ASK RX receiver
- 2 x grove I2C connector to connect other I2C devices
- 2 onboard nice WS2812 RGB LED

Boards V1.0 works but I needed a fix for RMF69 pin connection to ESP826 GPIO, let me explain :    
ESP8266 to boot correctly needs some pins at defined level, GPIO15 must be LOW and GPIO2 must be HIGH. Unfortunatlly with RFM69 connected as IRQ to GPIO2 and SS to GPIO15 it does not boot because RF69 pull it DIO IRQ to LOW, making GPIO2 LOW and ESP8266 not booting. The fix is to reverse the wiring, connect IRQ to GPIO15 and SS to GPIO2 (and do according changes in the code).

This page has been updated to reflect the GPIO changes and the PCB also, it's now V1.1.

*Boards V1.1 are in progress, I did not tested them yet, I will update as soon has I got them in my hands. Use at your own risks*

Detailed Description
====================

No specific documentation for now, but very close in term of feature to Particle Gateway I created and blogged on this dedicated [post][1]

### Schematic  
![schematic](https://raw.githubusercontent.com/hallard/NodeMCU-Gateway/master/NodeMCU-Gateway-sch.png)  

### Boards  
<img src="https://raw.githubusercontent.com/hallard/NodeMCU-Gateway/master/NodeMCU-Gateway-top.png" alt="Top" width="60%" height="60%">    

<img src="https://raw.githubusercontent.com/hallard/NodeMCU-Gateway/master/NodeMCU-Gateway-bottom.png" alt="Bottom" width="60%" height="60%">     

You can order the PCB of this board at [OSHPARK][3] (V1.0)

### Assembled boards

<img src="https://raw.githubusercontent.com/hallard/NodeMCU-Gateway/master/NodeMCU-Gateway-Top.jpg" alt="Top" width="75%" height="75%">    

<img src="https://raw.githubusercontent.com/hallard/NodeMCU-Gateway/master/NodeMCU-Gateway-Bottom.jpg" alt="Bottom" width="75%" height="75%">     

With a nice 1.3" Oled display    
<img src="https://raw.githubusercontent.com/hallard/NodeMCU-Gateway/master/NodeMCU-Gateway-OLED.jpg" alt="OLED" width="75%" height="75%">    

I'm currently waiting for boards V1.1 from OSHPARK

##License

You can do whatever you like with this design.

##Misc
See news and other projects on my [blog][2] 
 
[1]: https://hallard.me/particle-gateway/
[2]: https://hallard.me
[3]: https://oshpark.com/shared_projects/tHSjDP1w
