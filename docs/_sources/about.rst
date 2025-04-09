DualMCU ONE 
==============================

Introduction
------------
The DualMCU ONE development board is a versatile platform that combines the power of two microcontrollers: the RP2040 and the ESP32. This combination allows developers to take advantage of the unique features and capabilities of each microcontroller, making it ideal for a wide range of applications.

.. warning::
  The DualMCU-ONE operates with 3.3V logic levels instead of the Arduino Uno’s typical 5V.
  Make sure any shield or peripheral connected is compatible with 3.3V logic to avoid potential damage.

.. _figure_dualmcu_one2:
.. figure:: /_static/product/IMG_3145.jpg
   :align: center
   :alt: DualMCU ONE
   :width: 70%
   
   DualMCU ONE board 

The desing is inspired by the connections of Arduino UNO Rev3 , making it easy to use with a wide range of shields and accessories. The board also features a USB-C connector for power and data, a microSD card slot.

Squematic of the DualMCU ONE board
-----------------------------------

.. raw:: html

   <div style="text-align: center;">
      <button style="background-color: #87cefa; color: white; border: none; padding: 10px 20px;" onclick="window.open('./_static/DualMCU_R-ONE_V2.pdf', '_blank')">UNIT DualMCU R-ONE</button>
   </div>
   <br> </br>
   <iframe src="./_static/DualMCU_R-ONE_V2.pdf" style="width:100%; height:500px;" frameborder="0"></iframe>
   <br> </br>

Pin Mapping
------------

Digital and analog pins on the DualMCU ONE board are mapped to the corresponding GPIO pins on the RP2040 microcontroller.
This mapping allows you to easily identify the pins you need to use for your project.

Distribution of analog pins
~~~~~~~~~~~~~~~~~~~~~~~~~~~

Analog pins A0 to A3, TX1, and RX1 are mapped to the corresponding GPIO pins on the RP2040 microcontroller.

.. _figure_adc_pins:
.. figure:: /_static/pins_mapping_adc.png
   :align: center
   :alt: Dual
   :width: 50%

   DualMCU ONE pins A0 to A3, TX1, RX1

.. list-table:: Analog Pin Mapping
   :widths: 20 20
   :header-rows: 1
   :align: center

   * - PIN BOARD
     - GPIO RP2040
   * - A0
     - 26
   * - A1
     - 27
   * - A2
     - 28
   * - A3
     - 29
   * - TX1 / SDA0
     - 22
   * - RX1 / SCL0
     - 23

Distribution of digital pins D0 to D7
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. _figure_pins2:
.. figure:: /_static/pins_mapping1.png
   :align: center
   :alt: Dual
   :width: 50%

   DualMCU ONE pins D0 to D7

.. list-table:: Digital Pin Mapping
   :widths: 20 20 20
   :header-rows: 1
   :align: center

   * - PIN BOARD
     - Special Function
     - GPIO RP2040
   * - D0
     - RX0
     - GPIO1
   * - D1 
     - TX0
     - GPIO0
   * - D2 
     - RX1
     - GPIO5
   * - D3 
     - TX1
     - GPIO4
   * - D4 
     - *
     - GPIO9
   * - D5
     - *
     - GPIO11
   * - D6
     - *
     - GPIO8
   * - D7
     - *
     - GPIO10

Distribution of digital pins D8 to D13
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. _figure_pins:
.. figure:: /_static/pins_mapping.png
   :align: center
   :alt: Dual
   :width: 50%

   DualMCU ONE pins D8 to D13 

.. list-table:: Digital Pin Mapping 2
   :widths: 20 20 20
   :header-rows: 1
   :align: center

   * - PIN BOARD
     - Special Function
     - GPIO RP2040
   * - D8
     - *
     - GPIO2
   * - D9
     - *
     - GPIO3
   * - D10
     - *
     - GPIO17
   * - D11
     - *
     - GPIO19
   * - D12
     - *
     - GPIO16
   * - D13
     - *
     - GPIO18
   * - SDA0
     - *
     - GPIO20
   * - SCL0
     - *
     - GPIO21
   

RP2040 Microcontroller
----------------------
The RP2040 is a powerful microcontroller featuring a dual-core ARM Cortex-M0+ processor, 264KB of SRAM, and a wide range of peripherals.

.. _figure_rp2040:

.. figure:: /_static/Raspberry-pi.jpg
   :align: center
   :alt: RP2040
   :width: 40%
   
   RP2040 chip
 

The **RP2040** is Raspberry Pi's microcontroller, engineered to deliver high performance, cost-efficiency, and user-friendliness within the microcontroller domain.

Features
~~~~~~~~
The RP2040 boasts several advanced features, including:

- **Symmetrical Dual-Core Processor**: Equipped with dual ARM Cortex-M0+ processors operating at 133MHz.
- **Large On-Chip Memory**: 264kB of SRAM divided into six independent banks.
- **Deterministic Bus Fabric**: Ensures reliable and predictable operation.
- **Rich Peripheral Set**: Enhanced with Raspberry Pi's unique Programmable I/O (PIO) subsystem.

Professional users will find the RP2040's power and flexibility unrivaled, thanks to its comprehensive documentation, polished MicroPython port, and UF2 bootloader in ROM, which lowers the entry barrier for beginners and hobbyists.

Memory and Storage
~~~~~~~~~~~~~~~~~~

The RP2040 is a stateless device supporting cached execute-in-place from external QSPI memory. This design allows users to choose the appropriate density of non-volatile storage for their applications, benefiting from the low pricing of standard flash parts.

Manufacturing and Power Efficiency
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Manufactured on a modern 40nm process node, the RP2040 delivers:

- **High Performance**
- **Low Dynamic Power Consumption**
- **Minimal Leakage**

It includes various low-power modes, enabling extended-duration operation on battery power.

Technical Specifications
~~~~~~~~~~~~~~~~~~~~~~~~

**Key Features:**

- **Dual ARM Cortex-M0+ @ 133MHz**
- **264kB on-chip SRAM** in six independent banks
- **Support for up to 16MB of off-chip Flash memory** via dedicated QSPI bus
- **DMA controller**
- **Fully-connected AHB crossbar**
- **Interpolator and integer divider peripherals**
- **On-chip programmable LDO** to generate core voltage
- **2 on-chip PLLs** to generate USB and core clocks
- **30 GPIO pins**, 4 of which can be used as analog inputs

**Peripherals:**

- **2 UARTs**
- **2 SPI controllers**
- **2 I2C controllers**
- **16 PWM channels**
- **USB 1.1 controller and PHY**, with host and device support
- **8 PIO state machines**

.. tip::
   For more information about the RP2040 microcontroller, refer to the official documentation available on the `Raspberry Pi website <https://www.raspberrypi.com/documentation/microcontrollers/rp2040.html>`_.

ESP32 Microcontroller
---------------------

The **ESP32** was initially released in September 2016 by Espressif Systems. Since then, it has gained immense popularity in the hardware development and IoT project communities due to its versatility, power, and affordability. It is used in a wide range of applications, from home projects to industrial solutions.

.. _figure_esp32:
.. figure:: /_static/esp32.jpg
   :align: center
   :alt: ESP32
   :width: 40%
   
   ESP32 chip


The ESP32 is a series of low-cost, low-power microcontrollers with integrated Wi-Fi and Bluetooth capabilities. Developed by Espressif Systems, it is widely used in various Internet of Things (IoT) applications, including home automation, wearable devices, and industrial automation. The ESP32 offers a rich set of peripherals, including GPIO, SPI, I2C, UART, ADC, DAC, and more, making it versatile for a wide range of projects. Its popularity stems from its affordability, flexibility, and robustness. Developers often use the Arduino IDE or the ESP-IDF (Espressif IoT Development Framework) to program the ESP32.

Specifications
~~~~~~~~~~~~~~~~~~~~~~~~

The specifications of the ESP32 can vary slightly between different variants and models, but here is an overview of common features:

**Microcontroller**: Dual-core Tensilica LX6/LX7 microprocessor

**Clock Speed**: Up to 240 MHz

**RAM**: 520 KB to 4 MB

**Flash Memory**: 4 MB to 16 MB

**Wi-Fi**: 802.11 b/g/n (2.4 GHz)

**Bluetooth**: Bluetooth 4.2 and Bluetooth 5.0 BLE (Bluetooth Low Energy)

Peripherals
~~~~~~~~~~~~~~~~~~~~~~~~

- **GPIO (General Purpose Input/Output)**
- **SPI (Serial Peripheral Interface)**
- **I2C (Inter-Integrated Circuit)**
- **UART (Universal Asynchronous Receiver-Transmitter)**
- **ADC (Analog to Digital Converter)**
- **DAC (Digital to Analog Converter)**
- **PWM (Pulse Width Modulation)**
- **RTC (Real Time Clock)**
- **Touch sensor**
- **Interrupt controller**

Security
~~~~~~~~~~~~~~~~~~~~~~~~

Support for cryptography, including SSL/TLS, WPA/WPA2, and AES.

Power Consumption
~~~~~~~~~~~~~~~~~~~~~~~~

Low-power modes to conserve battery life in IoT applications.

Development Interfaces
~~~~~~~~~~~~~~~~~~~~~~~~

Compatible with the Arduino IDE and Espressif's ESP-IDF for software development.

Physical Dimensions
~~~~~~~~~~~~~~~~~~~~~~~~

Dimensions vary depending on the specific module, but they are generally compact and suitable for embedded applications.

.. caution::
   These are the general specifications; however, depending on the manufacturer and the exact model of the ESP32, there may be differences in specific features and additional capabilities.

