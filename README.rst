
Introduction
============

.. image:: https://readthedocs.org/projects/circuitpython-veml6070/badge/?version=latest

    :target: https://circuitpython-veml6070.readthedocs.io/

    :alt: Documentation Status

.. image :: https://img.shields.io/discord/327254708534116352.svg
    :target: https://discord.gg/nBQh6qu
    :alt: Discord

CircuitPython driver for the `VEML6070 UV Index Sensor Breakout <https://www.adafruit.com/product/2899>`_

Dependencies
=============
This driver depends on:

* `Adafruit CircuitPython <https://github.com/adafruit/circuitpython>`_
* `Bus Device <https://github.com/adafruit/Adafruit_CircuitPython_BusDevice>`_


Please ensure all dependencies are available on the CircuitPython filesystem.
This is easily achieved by downloading
`the Adafruit library and driver bundle <https://github.com/adafruit/Adafruit_CircuitPython_Bundle>`_.

Usage Example
=============  

.. code-block:: python

    import busio
    import veml6070
    import time
    from board import *

    with busio.I2C(SCL, SDA) as i2c:
        uv = veml6070.VEML6070(i2c)
        # Alternative constructors with parameters
        #uv = veml6070.VEML6070(i2c, 'VEML6070_1_T')
        #uv = veml6070.VEML6070(i2c, 'VEML6070_HALF_T', True)

        # take 10 readings
        for j in range(10):
            uv_raw = uv.read
            risk_level = uv.get_index(uv_raw)
            print('Reading: {0} | Risk Level: {1}'.format(uv_raw, risk_level))
            time.sleep(1)

API Reference
=============

.. toctree::
   :maxdepth: 2

   api

Contributing
============

Contributions are welcome! Please read our `Code of Conduct
<https://github.com/sommersoft/CircuitPython_veml6070/blob/master/CODE_OF_CONDUCT.md>`_
before contributing to help this project stay welcoming.

Building locally
================

To build this library locally you'll need to install the
`circuitpython-build-tools <https://github.com/adafruit/circuitpython-build-tools>`_ package.

.. code-block:: shell

    python3 -m venv .env
    source .env/bin/activate
    pip install circuitpython-build-tools

Once installed, make sure you are in the virtual environment:

.. code-block:: shell

    source .env/bin/activate

Then run the build:

.. code-block:: shell

    circuitpython-build-bundles --filename_prefix circuitpython-veml6070 --library_location .