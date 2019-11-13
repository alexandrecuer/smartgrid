As I was developping Themis further on, Cerema teams requested the integration of window opening/closing sensors into the system, 
in connection with their work on indoor air quality.
Measuring indoor air quality without knowing whether windows are open or closed makes little sense.

A first test was done with the Sonoff DW1, a door intrusion sensor that can detect the opening status.
The DW1 sensor is designed to send its radio payloads to a [Sonoff RF Bridge 433](https://www.itead.cc/wiki/Sonoff_RF_Bridge_433), which works as a Wifi/radio hub, embedding a lowcost ESP8285 microchip that can be easily reprogrammed. The 433 Mhz radio communication is managed by an 8 bit microcontroller EFM8BB10F8G from siliconlabs (associated to a SYN470R [superheterodyne receiver](https://en.wikipedia.org/wiki/Superheterodyne_receiver) from Synoxo). The interesting part is that the ESP8285 can communicate with the EFM8BB10 with a protocol described by Itead and called [RF universal transceiver module serial protocol](https://www.itead.cc/wiki/images/5/5e/RF_Universal_Transeceive_Module_Serial_Protocol_v1.0.pdf)

Some github projects focused on developping some excellent opensource firmwares for the Sonoff RF Bridge 533, 
