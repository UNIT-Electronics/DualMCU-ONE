Analog to Digital Conversion
============================

Learn how to read analog sensor values using the ADC module on the DualMCU ONE board. This section will cover the basics of analog input and conversion techniques.


.. _figure_adc:

.. figure:: /_static/adc.png
   :align: center
   :alt: ADC
   :width: 20%

   ADC Pins

ADC Definition
---------------------

Analog-to-digital conversion (ADC) is a process that converts analog signals into digital values. The DualMCU ONE development board, equipped
with the RP2040 microcontroller, includes four analog pins. These pins are capable of reading analog voltages and converting them into digital
values. Below you will find the details on how to utilize these pins for ADC operations.

Quantification and Codification of Analog Signals
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Analog signals are continuous signals that can take on any value within a given range. Digital signals, on the other hand, 
are discrete signals that can only take on specific values. 
The process of converting an analog signal into a digital signal involves two steps: quantification and codification.

- **Quantification**: This step involves dividing the analog signal into discrete levels. The number of levels determines the resolution of the ADC. 
  For example, an 8-bit ADC can divide the analog signal into 256 levels.

- **Codification**: This step involves assigning a digital code to each quantization level. The digital code represents the value of the analog signal at that level.

Distribution of Pins
---------------------
Below is a table showing the distribution of analog pins on the DualMCU board along with their corresponding GPIO pins on the RP2040.

.. list-table:: Pin Mapping
   :widths: 10 20
   :header-rows: 1
   :align: center

   * - PIN
     - GPIO RP2040
   * - A0
     - 26
   * - A1
     - 27
   * - A2
     - 28
   * - A3
     - 29

ADC includes four pins: A0, A1, A2, and A3. These pins can be used to read analog values from sensors and other devices. 
RP2040 has a 12-bit ADC, which means it can read analog values from 0 to 4095.
 
.. caution::
  
    The fourth analog channel (A3) on the RP2040 microcontroller is dedicated to the internal temperature sensor and is not available for external connections.

Class ADC
---------------------

The ``machine.ADC`` class is used to create ADC objects that can interact with the analog pins.

.. class:: machine.ADC(pin)

   The constructor for the ADC class takes a single argument: the pin number.

Example Definition
---------------------

To define and use an ADC object, follow this example:

.. tabs::

  .. tab:: MicroPython

    .. code-block:: python

      import machine
      adc = machine.ADC(0)  # Initialize ADC on pin A0

  .. tab:: C++

    .. code-block:: cpp

        #define ADC0 26



Reading Values
---------------------

To read the analog value converted to a digital format:


.. tabs:: 

  .. tab:: MicroPython

    .. code-block:: python

      adc_value = adc_value = adc.read() # Read the ADC value
      print(adc_value)  # Print the ADC value

  .. tab:: C++

    .. code-block:: cpp

      voltage_write = analogRead(ADC0);


Example Code
---------------------

Below is an example that continuously reads from an ADC pin and prints the results:

.. note:: 
    The following code is designed to work with the RP2040 microcontroller on the DualMCU development board.

.. tabs::
    
    .. tab:: MicroPython
  
      .. code-block:: python
  
        import machine
        import time
  
        # Setup
        A0 = machine.Pin(26, machine.Pin.IN)  # Initialize pin A0 for input
        adc = machine.ADC(A0)                 # Create ADC object
  
        # Continuous reading
        while True:
            adc_value = adc.read_u16()        # Read the ADC value
            print(f"ADC Reading: {adc_value:.2f}")  # Print the ADC value
            time.sleep(1)                     # Delay for 1 second   
  
    .. tab:: C++
  
      .. code-block:: cpp

        // Potentiometer is connected to GPIO 26 (Analog ADC0)
        const int potPin = 26;

        // variable for storing the potentiometer value
        int potValue = 0;

        void setup() {
          Serial.begin(115200);
          analogReadResolution(12);
          delay(1000);
        }

        void loop() {
          // Reading potentiometer value
          potValue = analogRead(potPin);
          Serial.println(potValue);
          delay(500);
        }