
SPI (Serial Peripheral Interface)
==================================

Explore SPI communication protocol and learn how to interface with SPI devices using the DualMCU ONE board. Well walk you through setting up SPI communication and 
communicating with SPI devices.


SPI Overview
----------------

SPI (Serial Peripheral Interface) is a synchronous, full-duplex, master-slave communication bus. It is commonly used to connect microcontrollers to peripherals such as sensors, displays, and memory devices. The DualMCU ONE development board features SPI communication capabilities, allowing you to interface with a wide range of SPI devices.

Pinout Details
----------------

In the next figure, you can see the SPI pins on the DualMCU ONE board and the corresponding GPIO pins on the ESP32 and RP2040 microcontrollers.

.. _figura-spi:

.. figure:: /_static/product/spi_uart.png
   :align: center
   :alt: SPI
   :width: 90%

   SPI Pins

Below is the pinout table for the SPI connections on the DualMCU ONE, detailing the corresponding GPIO connections for both the ESP32 and RP2040 microcontrollers.

.. list-table:: SPI Pinout
   :widths: 20 20 20
   :header-rows: 1
   :align: center

   * - PIN
     - GPIO ESP32
     - GPIO RP2040
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
   ESP32 and RP2040 have conections sharing the same pins, so you recommend to use only one microcontroller at a time.
   
   .. list-table:: sharing pins
      :widths: 20 20 
      :header-rows: 1
      :align: center

      * - GPIO ESP32
        - GPIO RP2040
      * - 5
        - 13
      * - 18
        - 14
      * - 23
        - 12

SPI between ESP32 & RP2040
---------------------------------------

DualMCU ONE board  was designed to be compatible with both ESP32 and RP2040 microcontrollers.  So it is possible to share information between the two microcontrollers 
using the SPI protocol. For this, we will use the following pins:

.. list-table:: SPI Connections
   :widths: 25 25 25 25
   :header-rows: 1
   :align: center

   * - Pin 
     - SPI RP2040
     - Pin 
     - SPI ESP32
   * - SCK
     - 14
     - SCK
     - 18
   * - MISO 
     - 12
     - MOSI
     - 23
   * - MOSI 
     - 15
     - MISO
     - 14
   * - SS
     - 13
     - SS
     - 5
   * - READY
     - 7
     - READY
     - 33
   * - RESET
     - 16
     - RESET
     - RST 


.. caution::
  The connection RST does not exist physically; therefore, it is necessary to establish an external connection. 
 












SDCard SPI
------------

.. warning::

    Ensure that the Micro SD contain data. We recommend saving multiple files beforehand to facilitate the use.


.. _figura-micro-sd-card:

.. figure:: /_static/Micro-SD-Card-Pinout.png
   :align: center
   :alt: Micro SD Card Pinout
   :width: 40%

   Micro SD Card Pinout

Library (MicroPython)
~~~~~~~~~~~~~~~~~~~~~~


The `dualmcu.py` library for MicroPython on ESP32 & RP2040 is compatible with the reader and writer of the Micro SD card. The library provides a simple interface for reading and writing files on the SD card. 
The library is available on PyPi and can be installed using the Thonny IDE.

**Installation**

1. Open `Thonny <https://thonny.org/>`_.
2. Navigate to **Tools** -> **Manage Packages**.
3. Search for ``dualmcu`` and click **Install**.

for more information, Check the section 

   - DualMCU ONE Library

Alternatively, download the library from `dualmcu.py <https://pypi.org/project/dualmcu/>`_.


VSPI & HSPI
**VSPI Interfacing.**
.. _figura-micro-sd-card-reader:

.. figure:: /_static/Lector-Micro-SD.jpg
  :align: center
  :alt: Micro SD Card reader
  :width: 40%

  Micro SD Card external reader

The conections are as follows:

This table illustrates the connections between the SD card and the GPIO pins on the ESP32 and RP2040 microcontrollers.

.. list-table:: VSPI Connections
  :widths: 10 20 20 20
  :header-rows: 1
  :align: center

  * - SD Card
    - Pin Name
    - ESP32
    - RP2040
  * - D3
    - SS
    - 5
    - 17
  * - CMD
    - MOSI
    - 23
    - 19
  * - VSS
    - GND
    - 
    - 
  * - VDD
    - 3.3V
    - 
    - 
  * - CLK
    - SCK
    - 18
    - 18
  * - D0
    - MISO
    - 19
    - 16

Descriptions
"""""""""""""
    - SCK (Serial Clock)
    - SS (Slave Select)


.. code-block:: python

  import machine, os
  from dualmcu import *

  SCK_PIN = 18
  MOSI_PIN = 23
  MISO_PIN = 19
  CS_PIN = 5

  spi = machine.SPI(1, baudrate=100000, polarity=0, phase=0, sck=machine.Pin(SCK_PIN), mosi=machine.Pin(MOSI_PIN), miso=machine.Pin(MISO_PIN))
  spi.init()
  sd = SDCard(spi, machine.Pin(CS_PIN))
  os.mount(sd, '/sd')
  os.listdir('/')

  print("files ...")
  print(os.listdir("/sd"))


**HSPI Interfacing.**

This table details the connections between the SD card and the ESP32 microcontroller.

.. list-table:: HSPI Connections
  :widths: 10 20 20
  :header-rows: 1
  :align: center


  * - SD Card
    - ESP32
    - PIN
  * - D2
    - 
    - 12
  * - D3
    - SS (Slave Select)
    - 13
  * - CMD
    - MOSI
    - 15
  * - VSS
    - GND
    -
  * - VDD
    - 3.3V
    - 
  * - CLK
    - SCK (Serial Clock)
    - 14
  * - VSS
    - GND
    - 
  * - D0
    - MISO
    - 2
  * - D1
    - 
    - 4



For the test , we will utilize an ESP32 WROM-32E and a  SanDisk Micros Ultra card with a capacity of 32 GB. 

.. code-block:: python

  import machine
  import os
  from dualmcu import *

  # Initialize SPI interface for the SD card
  spi = machine.SPI(2, baudrate=1000000, polarity=0, phase=0, sck=machine.Pin(14), mosi=machine.Pin(15), miso=machine.Pin(2))

  # Initialize the SD card
  sd = SDCard(spi, machine.Pin(13))

  # Mount the filesystem
  vfs = os.VfsFat(sd)
  os.mount(vfs, "/sd")

  # List files in the root of the SD card
  print("Files in the root of the SD card:")
  print(os.listdir("/sd"))


  os.umount("/sd") 


SPI (Arduino IDE)
~~~~~~~~~~~~~~~~~~

Arduino IDE is compatible for reader and writer of the Micro SD card. The library provides a simple interface for reading and writing files on the SD card.


.. tabs::

  .. tab:: VSPI 

    .. code-block::
      