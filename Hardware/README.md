
# Hadware [DualMCU-ONE](https://github.com/UNIT-Electronics/DualMCU-ONE) 


<a href="https://github.com/UNIT-Electronics/DualMCU-ONE/blob/main/Hardware/UE0022_DualMCU-ONE_v2.4_Schematic.pdf"><img src="Resources/Schematics_icon.jpg?raw=false" width="500px"><br/> Schematics</a>

# Power Tree

<img src="Resources/PowerTree.png?raw=false" width="1000px"><br/>

# Block Diagram

<img src="Resources/Block Diagram.png?raw=false" width="800px"><br/>

# Pinout

<img src="Resources/Pinout_Top[EN].jpg?raw=false" width="1000px"><br/>

<img src="Resources/Pinout_Btm[EN].jpg?raw=false" width="1000px"><br/>

# Board Topology

**Front View**<img src="Resources/TOP TOPOLOGY.png?raw=false" width="800px"><br/>

| Ref.  | Description                                     | Ref.  | Description                                         |
|-------|-------------------------------------------------|-------|---------------------------------------------------|
| U1    | Raspberry Pi RP2040 Microcontroller            | U4    | CH340C USB Bus Convert IC                         |
| U2    | Espressif ESP32 WROOM Wi-Fi/Bluetooth® Module  | U5    | HUB USB IC                                        |
| U3    | W25Q16JVUXIQ 2MB Flash IC                      | U6    | NCP1117ST33T3G 3.3V LDO Voltage Regulator         |
| U7    | MP1482DS-LF-Z DC/DC Converter                  | U8    | TCAN1051HVD CAN BUS Transceiver                   |
| L1    | Power On LED                                   | L2    | Built-in LED                                      |
| L3    | TX LED                                         | L4    | RX LED                                            |
| L5    | RGB-2020 LED                                   | L6    | WS2812B-3030 LED                                  |
| J1    | Male USB Type C Connector                      | J2    | Power Jack Connector                              |
| PB1   | RP2040 Reset Button                            | PB2   | RP2040 Boot Button                                |
| PB3   | ESP32 Flash Button                             | PB4   | ESP32 Reset Button                                |
| JP1   | ESP32 SYSTEM AND UART Header                  | JP2   | ESP32 SPI Header                                  |
| JP3   | RP2040 SPI Header                              | JP4   | JP4-1,JP4-2,JP4-3,JP4-4: Female Headers 2.54mm, compatible with Arduino UNO Pinout |
| JST1  | ESP32 UART JST Connector                       | JST2  | ESP32 I2C-QWIIC JST Connector                     |
| JST3  | AUX USB COMY JST Connector                     | JST4  | AUX USB COMX JST Connector                        |
| JST5  | RP2040 JST-3P Debugging Connector              | JST6  | RP2040 I2C-QWIIC JST Connector                    |
| SW1   | UART DIP Switch                                |       |                                                   |

**Back View**<img src="Resources/BOTTOM TOPOLOGY.png?raw=false" width="800px"><br/>

| Ref.  | Description                                     | Ref.  | Description                                         |
|-------|-------------------------------------------------|-------|---------------------------------------------------|
| X1    | Auxiliary MicroSD Card Connector               | X2    | Auxiliary FPC-24P Connector                       |
| SB1   | RP2040 to ESP32_RST Solder Bridge (disconnected)| SB2   | 120R CAN BUS Resistor Solder Bridge (disconnected)|
| SB3   | Steps ADC3 Leakage Solder Bridge (disconnected)| SB4   | ESP32-IO14 to RP2040-GPIO15 Solder Bridge (connected) |
| TP1   | USB D- Test Point                              | TP2   | USB D+ Test Point                                 |



For more details, check out the product pages at
* https://uelectronics.com/
