.. DualMCU ONE documentation master file, created by
   sphinx-quickstart on Thu Apr 25 11:08:12 2024.
   You can adapt this file completely to your liking, but it should at least
   contain the root `toctree` directive.



DualMCU ONE Getting Started
============================

.. note::
   
   The information in this file is subject to change without notice to improve or correct the documentation as needed.

.. tip::
   
	You are  reading the most recent version available. 


This guide is designed to help developers familiarize themselves with the DualMCU ONE development board and its capabilities. Whether you’re a beginner or an experienced developer, this guide will provide you with the knowledge and resources you need to start developing with the DualMCU ONE.


.. warning::
   The DualMCU ONE uses 3.3V logic levels, unlike the Arduino Uno, which operates at 5V. 
   Ensure that any connected shields or peripherals are compatible with 3.3V logic to prevent damage.

.. _figura3-dualmcu-one:

.. figure::  /_static/product/IMG_3136.jpg
   :align: center
   :alt: DualMCU ONE
   :width: 60%

   DualMCU ONE board





.. raw:: html

   <div style="text-align: center;">
      <button style="background-color: #77dd77; color: white; border: none; padding: 10px 20px; margin-right: 10px;" onclick="window.open('./_static/dualmcuone.pdf', '_blank')">Download PDF version</button>
   </div>


   
.. toctree::
   :maxdepth: 2
   :caption: Contents

   about
   pinout
   env
   lib
   gpio
   adc
   i2c
   jst
   spi
   WS2812
   communication
   upy
   duino
   report
   
   






Indices and tables
==================

* :ref:`genindex`
* :ref:`modindex`
* :ref:`search`