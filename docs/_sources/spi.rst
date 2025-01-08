SPI (Serial Peripheral Interface)
=================================

Explore SPI communication protocol and learn how to interface with SPI devices using the DualMCU ONE board. We'll guide you through setting up SPI communication and interfacing with SPI devices.

SPI Overview
------------

SPI (Serial Peripheral Interface) is a synchronous, full-duplex, master-slave communication bus. It is widely used to connect microcontrollers to peripherals like sensors, displays, and memory devices. The DualMCU ONE board supports SPI communication, enabling you to interface with a range of SPI devices.

Pinout Details
--------------

Below are the SPI pins for the DualMCU ONE board, including GPIO mappings for ESP32 and RP2040.

.. _figura-spi-esp32:

.. figure:: /_static/product/spi_esp32.png
   :align: center
   :alt: SPI Pinout Diagram
   :width: 90%

   SPI ESP32 Pinout Diagram



.. _figura-spi-rp2040:

.. figure:: /_static/product/spi_rp2040.png
   :align: center
   :alt: SPI Pinout Diagram
    :width: 90%

   SPI RP2040 Pinout Diagram

.. list-table:: SPI Pin Mappings
   :widths: 20 20 20
   :header-rows: 1
   :align: center

   * - Pin
     - ESP32 GPIO
     - RP2040 GPIO
   * - SCK
     - 18
     - 18
   * - MISO
     - 19
     - 16
   * - MOSI
     - 23
     - 19
   * - SS
     - 5
     - 17

.. caution::
   ESP32 and RP2040 share certain SPI pins. To avoid conflicts, use only one microcontroller at a time.

SPI Communication Example
--------------------------

Below is a basic example of initializing and using SPI with a Micro SD card in MicroPython:

.. code-block:: python

   import machine
   import os
   from dualmcu import *

   # Define SPI pins
   SCK_PIN = 18
   MOSI_PIN = 23
   MISO_PIN = 19
   CS_PIN = 5

   # Initialize SPI interface
   spi = machine.SPI(1, baudrate=100000, polarity=0, phase=0, sck=machine.Pin(SCK_PIN), mosi=machine.Pin(MOSI_PIN), miso=machine.Pin(MISO_PIN))

   # Initialize SD card
   sd = SDCard(spi, machine.Pin(CS_PIN))

   # Mount filesystem
   os.mount(sd, '/sd')

   # List files on the SD card
   print("Files on SD card:")
   print(os.listdir('/sd'))

   # Unmount SD card
   os.umount('/sd')

VSPI and HSPI Pin Configurations
--------------------------------

VSPI Connections
~~~~~~~~~~~~~~~~

The following table shows the VSPI pin connections for an external Micro SD card reader:

.. list-table:: VSPI Pin Mappings
   :widths: 10 20 20 20
   :header-rows: 1
   :align: center

   * - Pin
     - Name
     - ESP32 GPIO
     - RP2040 GPIO
   * - D3
     - SS
     - 5
     - 17
   * - CMD
     - MOSI
     - 23
     - 19
   * - CLK
     - SCK
     - 18
     - 18
   * - D0
     - MISO
     - 19
     - 16

HSPI Connections
~~~~~~~~~~~~~~~~

Below are the HSPI pin connections for the ESP32 microcontroller:

.. list-table:: HSPI Pin Mappings
   :widths: 10 20 20
   :header-rows: 1
   :align: center

   * - Pin
     - Name
     - ESP32 GPIO
   * - D3
     - SS
     - 13
   * - CMD
     - MOSI
     - 15
   * - CLK
     - SCK
     - 14
   * - D0
     - MISO
     - 2

.. caution::
   Ensure to use the correct SPI pins and avoid conflicts when sharing pins between peripherals.

Arduino IDE Compatibility
-------------------------

The Arduino IDE supports SPI communication and allows interfacing with Micro SD cards. Below is an example of using VSPI in Arduino:

.. tabs::

   .. tab:: VSPI

      .. code-block:: cpp

         #include <SPI.h>
         #include <SD.h>

         #define CS_PIN 5  // Chip Select pin for VSPI

         void setup() {
           Serial.begin(115200);
           if (!SD.begin(CS_PIN)) {
             Serial.println("Initialization failed!");
             return;
           }
           Serial.println("Initialization done.");
           File root = SD.open("/");
           while (true) {
             File entry = root.openNextFile();
             if (!entry) break;
             Serial.println(entry.name());
             entry.close();
           }
         }

         void loop() {}

