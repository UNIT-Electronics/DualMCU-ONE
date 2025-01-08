DualMCU Library (MicroPython)
=============================

DualMCU library is a project that aims to provide a set of tools to help developers work with the DualMCU ONE board.
The library is compatible with MicroPython on ESP32 & RP2040 and provides support for the SSD1306 display controller, Arduino Shields compatibility, and more.,


Installation
------------

1. Open `Thonny <https://thonny.org/>`_.
2. Navigate to **Tools** -> **Manage Packages**.
3. Search for ``dualmcu`` and click **Install**.

.. _figure_dualmcu_libary1:
.. figure:: /_static/dualmcu_library.png
   :align: center
   :alt: DualMCU Library
   :width: 60%
   
   DualMCU Library 1

4. Successfully installed the library.

.. _figure_dualmcu_libary_success_2:
.. figure:: /_static/dualmcu_library_success.png
   :align: center
   :alt: DualMCU Library
   :width: 60%
   
   DualMCU Library Successfully Installed

Alternatively, download the library from `dualmcu.py <https://pypi.org/project/dualmcu/>`_.


Usage
-----

The library provides a set of tools to help developers work with the DualMCU ONE board. The following are the main features of the library:

- **SSD1306 Display Controller**: The library provides support for the SSD1306 display controller, allowing developers to easily interface with OLED displays.

- **Arduino Shields Compatibility**: The library is compatible with Arduino Shields, making it easy to use a wide range of shields and accessories with the DualMCU ONE board.


.. code-block:: python

    import machine
    from dualmcu import *

    i2c = machine.SoftI2C( scl=machine.Pin(22), sda=machine.Pin(21))

    oled = SSD1306_I2C(128, 64, i2c)

    oled.fill(1)
    oled.show()

    oled.fill(0)
    oled.show()
    oled.text('UNIT', 50, 10)
    oled.text('ELECTRONICS', 25, 20)

    oled.show()

The library is actively maintained and updated to provide the best experience for developers working with the DualMCU ONE board. For more information and updates, visit the `dualmcu GitHub repositorY``