# DualMCU-ONE ESP32+RP2040 Microcontroller Board PCB

<a href="https://uelectronics.com/producto/unit-dualmcu-one-esp32-rp2040/"><img src="Resources/IMG_3134.jpg?raw=true" width="650px"><br/>
*Click here to purchase one from the UNIT Electronics shop*</a>

For more details, check out the product pages at:
* [UNIT Electronics Website](https://uelectronics.com/)
* [Hardware-DualMCU-ONE](https://github.com/UNIT-Electronics/DualMCU-ONE/tree/main/Hardware)
* [Product Reference Manual](https://github.com/UNIT-Electronics/DualMCU-ONE/blob/main/DualMCU-ONE(Product%20Reference%20Manual%20)%5BEN%5D.pdf)
* [DualMCU-ONE_Getting_Started](https://unit-electronics.github.io/DualMCU-ONE/index.html)

---

## Description

The **UNIT DualMCU-ONE** is a highly versatile development board that integrates the power of two microcontrollers: the ESP32 and the RP2040. Designed for advanced IoT, robotics, and industrial applications, it provides enhanced connectivity, robust power management, and full compatibility with Arduino UNO shields.

> ⚠️ **Important Note:**  
> The DualMCU-ONE operates with **3.3V logic levels** instead of the Arduino Uno’s typical 5V.  
> Make sure any shield or peripheral connected is compatible with 3.3V logic to avoid potential damage.

> ✅ **Arduino Uno Compatibility:**  
> The DualMCU-ONE is fully compatible with Arduino Uno shields.  
> Its female headers follow the same pin distribution as the Uno, making it easy to migrate existing projects or reuse accessories.  
> This makes it a perfect choice whether you're just starting out or already experienced with Arduino.


Key enhancements over its predecessor, the DualMCU, include:
- SPI communication between the MCUs for improved data transfer.
- A USB Type-C hub, replacing the USB communication switch.
- CAN bus connectivity for industrial and automotive environments.
- Onboard connectors compatible with STEMMA and QWIIC ecosystems.

---

## Features

- **Microcontrollers**:
  - **RP2040**: Dual-core ARM Cortex-M0+ at 133 MHz, compatible with Arduino UNO headers.
  - **ESP32**: Wi-Fi, Bluetooth, and CAN bus capabilities.

- **USB Connectivity**:
  - Integrated USB Type-C hub for simultaneous communication with both MCUs.
  - Additional USB device support via JST connectors.

- **Power Supply**:
  - Robust MP1482DS regulator, supporting input voltages up to 18V.
  - Delivers stable 5V output for powering peripherals.

- **Storage**:
  - Optional MicroSD socket (up to 64GB), connected via ESP32's QSPI interface.

- **I2C Connectors**:
  - JST-SH connectors compatible with STEMMA and QWIIC ecosystems.

- **Additional Features**:
  - RGB 2020 LED and WS2812B LED for visual feedback.
  - Optional FPC-24P connector for expanded ESP32 GPIO access.

---

## Applications

The **DualMCU-ONE** is ideal for:
- **Internet of Things (IoT)**: Wireless connectivity for smart devices.
- **Education**: Perfect for students and makers to explore advanced microcontrollers.
- **Industrial**: Robust CAN bus communication for automotive and industrial use.
- **Prototyping**: Full Arduino UNO shield compatibility.
- **Robotics**: Multi-core processing for complex systems.

Note: While the DualMCU-ONE is fully compatible with Arduino UNO shields in terms of pin layout, it operates at 3.3V logic levels, unlike the Arduino Uno which uses 5V. Always verify shield voltage compatibility before connecting.
---

## Getting Started

The **DualMCU-ONE** supports:
- **Arduino IDE** for both RP2040 and ESP32.
- **MicroPython** and **CircuitPython** with IDEs like Thonny.

For setup and first projects, refer to the [Getting Started Guide](https://unit-electronics.github.io/DualMCU-ONE/index.html).

---

## Development Resources

| Resource                                   | Link                                                                                   |
|-------------------------------------------|----------------------------------------------------------------------------------------|
| **Arduino Package RP2040 JSON**           | [RP2040 Package](https://github.com/UNIT-Electronics/Uelectronics-RP2040-Arduino-Package) |
| **Arduino Package ESP32 JSON**            | [ESP32 Package](https://github.com/UNIT-Electronics/Uelectronics-ESP32-Arduino-Package) |
| **MicroPython Documentation**             | [MicroPython.org](https://micropython.org/)                                            |
| **CircuitPython Documentation**           | [Adafruit CircuitPython](https://circuitpython.org/)                                   |
| **UNIT DualMCU-ONE Documentation**        | [DualMCU-ONE Documentation](https://github.com/UNIT-Electronics/DualMCU-ONE)          |
| **Getting Started with DualMCU-ONE**      | [DualMCU-ONE Guide](https://unit-electronics.github.io/DualMCU-ONE/index.html)        |
| **Thonny IDE**                            | [Thonny.org](https://thonny.org/)                                                     |
| **Arduino IDE**                           | [Arduino IDE](https://www.arduino.cc/en/software)                                     |
| **CH340 Driver**                          | [CH340 Driver](http://www.wch-ic.com/downloads/CH341SER_ZIP.html)                     |
| **Visual Studio Code**                    | [Visual Studio Code](https://code.visualstudio.com/download)                          |
| **Raspberry Pi Pico RP2040 Documentation**| [RP2040 Documentation](https://www.raspberrypi.com/documentation/microcontrollers/)   |
| **Raspberry Pi Pico Python SDK**          | [Python SDK](https://datasheets.raspberrypi.com/pico/raspberry-pi-pico-python-sdk.pdf) |
| **Raspberry Pi Pico MicroPython Examples**| [MicroPython Examples](https://github.com/raspberrypi/pico-micropython-examples)      |
| **Raspberry Pi Pico C/C++ SDK**           | [C/C++ SDK](https://www.raspberrypi.com/documentation/microcontrollers/c_sdk.html)    |
| **Raspberry Pi Pico C/C++ Examples**      | [C/C++ Examples](https://github.com/raspberrypi/pico-examples)                        |
| **RP2040 Datasheet**                      | [RP2040 Datasheet](https://datasheets.raspberrypi.com/rp2040/rp2040-datasheet.pdf)    |
| **ESP32 WROOM 8MB Datasheet**             | [ESP32 WROOM Datasheet](https://www.espressif.com/sites/default/files/documentation/esp32-wroom-32e_esp32-wroom-32ue_datasheet_en.pdf) |


---

## Contributions

We welcome contributions! Please review our [Contribution Guidelines](CONTRIBUTING.md) before submitting pull requests.

---

## License

This project is licensed under the [MIT License](LICENSE).
