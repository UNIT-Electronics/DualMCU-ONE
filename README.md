# DualMCU-ONE ESP32+RP2040 Microcontroller Board PCB

<a href="https://uelectronics.com/"><img src="Resources/IMG_3134.jpg?raw=true" width="650px"><br/>
*Click here to purchase one from the UNIT Electronics shop*</a>

For more details, check out the product pages at:
* [UNIT Electronics Website](https://uelectronics.com/)
* [Hardware-DualMCU-ONE](https://github.com/UNIT-Electronics/DualMCU-ONE/tree/main/Hardware)
* [Product Reference Manual.pdf](https://github.com/UNIT-Electronics/DualMCU-ONE/blob/main/DualMCU_ONE_Product_Reference_Manual.pdf)
* [DualMCU-ONE_Getting_Started](https://github.com/UNIT-Electronics/DualMCU-ONE_Getting_Started)

---

## Description

The **UNIT DualMCU-ONE** is a highly versatile development board that integrates the power of two microcontrollers: the ESP32 and the RP2040. Designed for advanced IoT, robotics, and industrial applications, it provides enhanced connectivity, robust power management, and full compatibility with Arduino UNO shields.

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

---

## Getting Started

The **DualMCU-ONE** supports:
- **Arduino IDE** for both RP2040 and ESP32.
- **MicroPython** and **CircuitPython** with IDEs like Thonny.

For setup and first projects, refer to the [Getting Started Guide](https://github.com/UNIT-Electronics/DualMCU-ONE_Getting_Started).

---

## Development Resources

| Resource                          | Link                                                                                   |
|-----------------------------------|----------------------------------------------------------------------------------------|
| **Arduino Package RP2040 JSON**   | [RP2040 Package](https://github.com/UNIT-Electronics/Uelectronics-RP2040-Arduino-Package) |
| **Arduino Package ESP32 JSON**    | [ESP32 Package](https://github.com/UNIT-Electronics/Uelectronics-ESP32-Arduino-Package) |
| **MicroPython Documentation**     | [MicroPython.org](https://micropython.org/)                                            |
| **CircuitPython Documentation**   | [Adafruit CircuitPython](https://circuitpython.org/)                                   |

---

## Contributions

We welcome contributions! Please review our [Contribution Guidelines](CONTRIBUTING.md) before submitting pull requests.

---

## License

This project is licensed under the [MIT License](LICENSE).
