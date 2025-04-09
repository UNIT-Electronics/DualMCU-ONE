Arduino Shields Compatibility
=============================

The DualMCU ONE board is compatible with a wide range of Arduino shields and accessories. The board features 
the same pinout as the Arduino UNO Rev3, making it easy to use with existing shields. 
The board also features a USB-C connector for power and data, a microSD card slot, and a dual-core architecture
with an RP2040 and an ESP32 microcontrollers.

.. warning::
    
   The DualMCU ONE board is designed to be compatible with Arduino shields, but not all shields may work perfectly due to differences in voltage levels and pin configurations. 
   Always check the specifications of the shield you are using to ensure compatibility.

.. _figure_dualmcu_one_n:
.. figure:: /_static/dualmcu_one.png
   :align: center
   :alt: DualMCU ONE
   :width: 60%
   
   DualMCU ONE board

Multi-purpose Shield for DualMCU ONE
------------------------------------    

.. _figure_multi_purpose_shield:
.. figure:: /_static/shields.png
   :align: center
   :alt: Multi-purpose Shield
   :width: 60%
   
   Multi-purpose Shield

The Multi-purpose Shield is a versatile accessory for the DualMCU ONE board. It features a variety of sensors and components, including:

- **2 LED indicators**: Show the program status.
- **2 switches**: For external interrupt experiments.
- **Reset button**: Allows resetting the board.
- **DHT11 sensor**: Measures temperature and humidity.
- **Potentiometer**: Provides analog input.
- **Passive buzzer**: Functions as an alarm.
- **Full-color RGB LED**: Provides multiple color options.
- **Photocell**: Detects the brightness of light.
- **LM35D temperature sensor**: Measures temperature.
- **Infrared receiver**: Enables infrared communication.
- **Digital pins**: 2 digital pins (D7 and D8).
- **Analog pin**: 1 analog pin (A3).
- **IIC interface**: For I2C communication.
- **TTL serial pin**: For serial communication.

.. warning::
   The Multi-purpose Shield ADC sensors are connected to a 5V voltage supply, so caution is needed when connecting them to the DualMCU ONE board.


.. code-block:: python

    from machine import Pin
    import time
    from dht import DHT11
    from dualmcu import *

    # Create an instance of Shield
    my_shield = Shield(
        pin_red=D9, pin_green=D10, pin_blue=D11,
        pin_buzzer=D5, pin_led1=D13, pin_led2=D12,
        pin_button1=D2, pin_button2=D3, pin_analog=A0
    )

    # Configure DHT11 sensor
    sensor_dht = DHT11(Pin(D4))

    try:
        while True:
            # Read DHT11 sensor
            sensor_dht.measure()
            temp_dht = sensor_dht.temperature()
            hum = sensor_dht.humidity()
            
            # Read analog sensor
            analog_value = my_shield.read_analog()
            
            # Print the values read
            print(f'Temperature: {temp_dht}°C Humidity: {hum}% Analog: {analog_value}')
            
            # Read buttons and control LEDs
            my_shield.set_led1(my_shield.read_button1() == 0)
            my_shield.set_led2(my_shield.read_button2() == 0)
            
            # Play a sequence of tones and change the LED colors
            for color, freq in zip(
                ['red', 'green', 'blue', 'yellow', 'cyan', 'magenta', 'white', 'off'],
                [262, 294, 330, 349, 392, 440, 494, 523]
            ):
                my_shield.set_led(color)
                my_shield.play_tone(freq, 0.5)
                time.sleep(0.1)

    except KeyboardInterrupt:
        my_shield.deinit()


