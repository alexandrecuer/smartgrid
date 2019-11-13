As I was developping Themis further on, Cerema teams requested the integration of window opening/closing sensors into the system, 
in connection with their work on indoor air quality.
Measuring indoor air quality without knowing whether windows are open or closed makes little sense.

A first test was done with the Sonoff DW1, a door intrusion sensor that can detect the opening status.
The DW1 sensor is designed to send its radio payloads to a [Sonoff RF Bridge 433](https://www.itead.cc/wiki/Sonoff_RF_Bridge_433), which works as a Wifi/radio hub, embedding a lowcost ESP8285 microchip that can be easily reprogrammed. The 433 Mhz radio communication is managed by an 8 bit microcontroller EFM8BB10F8G from siliconlabs (associated to a SYN470R [superheterodyne receiver](https://en.wikipedia.org/wiki/Superheterodyne_receiver) from Synoxo). The interesting part is that the ESP8285 can communicate with the EFM8BB10 with a protocol described by Itead and called [RF universal transceiver module serial protocol](https://www.itead.cc/wiki/images/5/5e/RF_Universal_Transeceive_Module_Serial_Protocol_v1.0.pdf)

Some github projects focused on developping opensource firmwares for the Sonoff RF Bridge 533, such as [openMQTTgateway](https://github.com/1technophile/OpenMQTTGateway) and [espurna](https://github.com/xoseperez/espurna)

With minimal effort, it is possible to use the sonoff DW1 in Themis or Emoncms

# adding a row of board to board connectors to use with an UART2USB programming cable
before soldering 
![before soldering](assets/before_soldering.jpg)
after soldering
![after soldering](assets/after_soldering.jpg)
bottom view after soldering
![after soldering bottom view](assets/after_soldering_bottom_view.jpg)

# backup the stock/factory firmware on the Sonoff RF bridge
This part will use the esptool which you can install easily
```
pip install esptool
```
a full article can be found : https://github.com/xoseperez/espurna/wiki

Before using esptool in cli you will need to connect the bridge to your computer in flashmode :

1) Connect the ESP8286 header to your USB2UART programmer (RX to TX, TX to RX and GND to GND)

2) Place the switch in the OFF position

3) Press and hold the reset button

4) And power the device either via the microUSB port or via the 3V3 pin on the same programming header

![connection to a UART2USB cable](assets/connection_to_UART.jpg)

red : 3V

black : ground

yellow : RX from the bridge

orange : TX from the bridge

You can get the firmware size with the command `esptool flash_id`  
```
esptool.py v2.8
Found 1 serial ports
Serial port COM4
Connecting....
Detecting chip type... ESP8266
Chip is ESP8285
Features: WiFi, Embedded Flash
Crystal is 26MHz
MAC: 84:0d:8e:66:92:4c
Uploading stub...
Running stub...
Stub running...
Manufacturer: 51
Device: 4014
Detected flash size: 1MB
Hard resetting via RTS pin...
```

The size being known, you can now backup the 1Mo firmware `esptool --port COM4 read_flash 0x00000 0x100000 esp-1MB-backup.bin`
```
esptool.py v2.8
Serial port COM4
Connecting....
Detecting chip type... ESP8266
Chip is ESP8285
Features: WiFi, Embedded Flash
Crystal is 26MHz
MAC: 84:0d:8e:66:92:4c
Uploading stub...
Running stub...
Stub running...
1048576 (100 %)
1048576 (100 %)
Read 1048576 bytes at 0x0 in 98.7 seconds (85.0 kbit/s)...
Hard resetting via RTS pin...
```

Image restoration can be achieved specifying the starting address:
```
esptool --port COM4 write_flash 0x00000 esp-1MB-backup.bin
```


