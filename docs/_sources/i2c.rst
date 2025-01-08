I2C (Inter-Integrated Circuit)
===============================

Discover the I2C communication protocol and learn how to communicate with I2C devices using the DualMCU ONE board. This section will cover I2C bus setup and communication with I2C peripherals.

.. _figure_i2c:

.. figure:: /_static/dualmcu_one3.png
   :align: center
   :alt: I2C
   :width: 90%

   I2C Pins

I2C Overview
------------

I2C (Inter-Integrated Circuit) is a synchronous, multi-master, multi-slave, packet-switched, single-ended, serial communication bus. It is commonly used to connect low-speed peripherals to processors and microcontrollers. The DualMCU ONE development board features I2C communication capabilities, allowing you to interface with a wide range of I2C devices.

Pinout Details
--------------
Below is the pinout table for the I2C connections on the DualMCU ONE, detailing the corresponding GPIO connections for both the ESP32 and RP2040 microcontrollers.

.. list-table:: I2C Pinout
   :widths: 20 20 20
   :header-rows: 1
   :align: center

   * - PIN
     - GPIO ESP32
     - GPIO RP2040
   * - SCLK
     - 22
     - 5 / 21 / 23
   * - SDA
     - 21
     - 4 / 20 / 22

Scanning for I2C Devices
------------------------
To scan for I2C devices connected to the bus, you can use the following code snippet:

.. tabs::

   .. tab:: MicroPython

      .. code-block:: python

         import machine

         i2c = machine.SoftI2C(0, scl=machine.Pin(5), sda=machine.Pin(4))
         devices = i2c.scan()

         for device in devices:
             print("Device found at address: {}".format(hex(device)))

   .. tab:: C++

      .. code-block:: cpp

        #include <Wire.h>

        void setup() {
          // in setup
          Wire.setSDA(4);
          Wire.setSCL(5);
          Wire.begin();
          Serial.begin(9600); // Start serial communication at 9600 baud rate
          while (!Serial); // Wait for serial port to connect
          Serial.println("\nI2C Scanner");
        }

        void loop() {
          byte error, address;
          int nDevices;

          Serial.println("Scanning...");

          nDevices = 0;
          for(address = 1; address < 127; address++ ) {
            // The i2c_scanner uses the return value of the Write.endTransmisstion to see if
            // a device did acknowledge to the address.
            Wire.beginTransmission(address);
            error = Wire.endTransmission();

            if (error == 0) {
              Serial.print("I2C device found at address 0x");
              if (address<16) 
                Serial.print("0");
              Serial.print(address, HEX);
              Serial.println("  !");

              nDevices++;
            }
            else if (error==4) {
              Serial.print("Unknown error at address 0x");
              if (address<16)
                Serial.print("0");
              Serial.println(address, HEX);
            }    
          }
          if (nDevices == 0)
            Serial.println("No I2C devices found\n");
          else
            Serial.println("done\n");

          delay(5000);           // wait 5 seconds for next scan
        }


SSD1306 Display
----------------

.. _figura-ssd1306-display:

.. figure:: /_static/oled.jpg
   :align: center
   :alt: ssd1306 display
   :width: 50%

   SSD1306 Display

The display 128x64 pixel monochrome OLED display equipped with an SSD1306 controller is connected using a JST 1.25mm 4-pin connector. The following table provides the pinout details for the display connection.

.. list-table:: SSD1306 Display Pinout
   :widths: 20 20
   :header-rows: 1
   :align: center

   * - Pin
     - Connection
   * - 1
     - GND
   * - 2
     - VCC
   * - 3
     - SDA
   * - 4
     - SCL

Library Support
~~~~~~~~~~~~~~~~

MicroPython
^^^^^^^^^^^

The `dualmcu.py` library for MicroPython on ESP32 & RP2040 is compatible with the SSD1306 display controller.

**Installation**

1. Open `Thonny <https://thonny.org/>`_.
2. Navigate to **Tools** -> **Manage Packages**.
3. Search for ``dualmcu`` and click **Install**.

for more information, Check the section 

.. toctree::
    :maxdepth: 1

    library

Alternatively, download the library from `dualmcu.py <https://pypi.org/project/dualmcu/>`_.



**Microcontroller Configuration**

.. code-block:: python
  
  SoftI2C(scl, sda, *, freq=400000, timeout=50000)

Change the following line depending on your microcontroller:

**For ESP32**::

    >>> i2c = machine.SoftI2C(freq=400000, timeout=50000, sda=machine.Pin(21), scl=machine.Pin(22))

**For RP2040**::

    >>> i2c = machine.SoftI2C(freq=400000, timeout=50000, sda=machine.Pin(4), scl=machine.Pin(5))


**Example Code**

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

This code initializes the display, fills the screen with different colors, and displays text.

``sda=machine.Pin(*)`` and ``scl=machine.Pin(*)`` should be replaced with the appropriate GPIO pins for your setup.


This version clarifies the structure, pin configurations, library usage, installation instructions, and example code for your project. Adjust the placeholders marked with 
`*` in your actual code based on your specific GPIO pin assignments.

C++

The `Adafruit_SSD1306` library for Arduino is compatible with the SSD1306 display controller.

**Installation**

1. Open the Arduino IDE.
2. Navigate to **Tools** -> **Manage Libraries**.
3. Search for ``Adafruit_SSD1306`` and click **Install**.

**Description code**

The provided Arduino sketch is designed to interface an RP2040 microcontroller with an SSD1306 OLED 
display using the I2C communication protocol. It begins by including the necessary libraries for 
controlling the display and initializing serial communication for debugging purposes. The sketch 
defines constants for the display dimensions and I2C pins (SDA on GPIO 4 and SCL on GPIO 5) and 
initializes an Adafruit SSD1306 object.

**Example Code**


.. code-block:: cpp
  
  #include <Wire.h>
  #include <Adafruit_GFX.h>
  #include <Adafruit_SSD1306.h>

  // OLED display TWI (I2C) interface
  #define OLED_RESET     -1 // Reset pin # (or -1 if sharing Arduino reset pin)
  #define SCREEN_WIDTH   128 // OLED display width, in pixels
  #define SCREEN_HEIGHT  64  // OLED display height, in pixels
  #define SDA_PIN        4   // SDA pin
  #define SCL_PIN        5   // SCL pin

  // Declare an instance of the class (specify width and height)
  Adafruit_SSD1306 display(SCREEN_WIDTH, SCREEN_HEIGHT, &Wire, OLED_RESET);

  void setup() {
    Serial.begin(9600);

    // Initialize I2C
    Wire.setSDA(4);
    Wire.setSCL(5);
    Wire.begin();
    // Start the OLED display
    if(!display.begin(SSD1306_SWITCHCAPVCC, 0x3C)) { // Address 0x3C for 128x64
      Serial.println(F("SSD1306 allocation failed"));
      for(;;); // Don't proceed, loop forever
    }

    // Clear the buffer
    display.clearDisplay();

    // Set text size and color
    display.setTextSize(1);
    display.setTextColor(SSD1306_WHITE);
    display.setCursor(0,0);
    display.println(F("UNIT ELECTRONICS!"));
    display.display();  // Show initial text
    delay(4000);        // Pause for 2 seconds
  }

  void loop() {
    // Increase a counter
    static int counter = 0;

    // Clear the display buffer
    display.clearDisplay();
    display.setCursor(0, 10); // Position cursor for new text
    display.setTextSize(2);   // Larger text size

    // Display the counter
    display.print(F("Count: "));
    display.println(counter);

    // Refresh the display to show the new count
    display.display();
    
    // Increment the counter
    counter++;

    // Wait for half a second
    delay(500);
  }

      


