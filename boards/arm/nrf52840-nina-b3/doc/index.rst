.. _nrf52840_aeler_nina_b3:

AELER NINAB3
####################

Overview
********

The AELER NINAB3 hardware provides support for the Nordic Semiconductor
nRF52840 ARM Cortex-M4F CPU and the following devices:

* :abbr:`ADC (Analog to Digital Converter)`
* CLOCK
* FLASH
* :abbr:`GPIO (General Purpose Input Output)`
* :abbr:`I2C (Inter-Integrated Circuit)`
* :abbr:`MPU (Memory Protection Unit)`
* :abbr:`NVIC (Nested Vectored Interrupt Controller)`
* :abbr:`PWM (Pulse Width Modulation)`
* RADIO (Bluetooth Low Energy and 802.15.4)
* :abbr:`RTC (nRF RTC System Clock)`
* Segger RTT (RTT Console)
* :abbr:`SPI (Serial Peripheral Interface)`
* :abbr:`UART (Universal asynchronous receiver-transmitter)`
* :abbr:`USB (Universal Serial Bus)`
* :abbr:`WDT (Watchdog Timer)`

.. figure:: img/NINAB3.jpg
     :width: 442px
     :align: center
     :alt: AELER NINAB3

     AELER NINAB3 (Credit: AELER Technologies SA)

More information about the board is available at wwww.aeler.com

Hardware
********

Proprietary AELER hardware interfacing with the u-blox NINA-B302

Supported Features
==================

The nrf52840_aeler_nina_b3 board configuration supports the following
hardware features currently:

+-----------+------------+----------------------+
| Interface | Controller | Driver/Component     |
+===========+============+======================+
| ADC       | on-chip    | adc                  |
+-----------+------------+----------------------+
| CLOCK     | on-chip    | clock_control        |
+-----------+------------+----------------------+
| FLASH     | on-chip    | flash                |
+-----------+------------+----------------------+
| GPIO      | on-chip    | gpio                 |
+-----------+------------+----------------------+
| I2C(M)    | on-chip    | i2c                  |
+-----------+------------+----------------------+
| MPU       | on-chip    | arch/arm             |
+-----------+------------+----------------------+
| NVIC      | on-chip    | arch/arm             |
+-----------+------------+----------------------+
| PWM       | on-chip    | pwm                  |
+-----------+------------+----------------------+
| RADIO     | on-chip    | Bluetooth,           |
|           |            | ieee802154           |
+-----------+------------+----------------------+
| RTC       | on-chip    | system clock         |
+-----------+------------+----------------------+
| RTT       | Segger     | console              |
+-----------+------------+----------------------+
| SPI(M/S)  | on-chip    | spi                  |
+-----------+------------+----------------------+
| UART      | on-chip    | serial               |
+-----------+------------+----------------------+
| USB       | on-chip    | usb                  |
+-----------+------------+----------------------+
| WDT       | on-chip    | watchdog             |
+-----------+------------+----------------------+

Connections and IOs
===================

LED
---

* LED0  = P0.13 (With pwm0 function)
* LED1  = P0.14
* LED2  = P0.15

Push buttons
------------

* Reset = SW0 = P0.18 (can be used as GPIO also)

UART_0
------

* TX = P0.6
* RX = P0.8
* RTS = P0.5
* CTS = P0.7

I2C_0
-----

I2C pins connected to onboard sensors:

* SDA = P0.26
* SCL = P0.27

SPI_1
-----

* SCK = P0.31
* MOSI = P1.29
* MISO = P1.1

Programming and Debugging
*************************

Applications for the ``nrf52840_aeler_nina_b3`` board configuration can be
built and flashed in the usual way (see :ref:`build_an_application`
and :ref:`application_run` for more details); The onboard Black Magic
Probe debugger presents itself as two USB-serial ports. On Linux,
they may come up as ``/dev/ttyACM0`` and ``/dev/ttyACM1``. The first
one of these (``/dev/ttyACM0`` here) is the debugger port.
GDB can directly connect to this port without requiring a GDB server by specifying
``target external /dev/ttyACM0``. The second port acts as a
serial port, connected to the SoC.

Flashing
========

Applications are flashed and run as usual (see :ref:`build_an_application` and
:ref:`application_run` for more details).

Here is an example for the :ref:`hello_world` application.

First, run your favorite terminal program to listen for output.

.. code-block:: console

   $ minicom -D <tty_device> -b 115200

Replace :code:`<tty_device>` with the serial port of Black Magic Probe.
For example, under Linux, :code:`/dev/ttyACM1`.

Then build and flash the application in the usual way.

.. zephyr-app-commands::
   :zephyr-app: samples/hello_world
   :board: nrf52840_aeler_nina_b3
   :goals: build flash

Debugging
=========

Debug and attach configurations are available using Black Magic Probe, and
``ninja debug``, or ``ninja attach`` (or with ``make``) are available.

NOTE: You may need to press the reset button once after using ``ninja flash``
to start executing the code. (not required with ``debug`` or ``attach``)


Testing the LEDs and buttons in the nRF52840 PDK
************************************************

There are 2 samples that allow you to test that the buttons (switches) and LEDs on
the board are working properly with Zephyr:

* :ref:`blinky-sample`
* :ref:`button-sample`

You can build and flash the examples to make sure Zephyr is running correctly on
your board. The button and LED definitions can be found in
:zephyr_file:`boards/arm/nrf52840_aeler_nina_b3/nrf52840_aeler_nina_b3.dts`.


References
**********

.. target-notes::

.. _AELER Technologies SA website: https://www.aeler.com
.. _Nordic Semiconductor Infocenter: http://infocenter.nordicsemi.com/
.. _U-blox NINA-B30x reference documentation: https://www.u-blox.com/en/product/nina-b3-series
.. _Black Magic Probe website: https://github.com/blacksphere/blackmagic
