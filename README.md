![Qwiic SerLCD Python Package](docs/images/gh-banner-py-qwiic-serlcd.png "qwiic SerLCD Python Package" )

# SparkFun Qwiic SerLCD - Python Package

![PyPi Version](https://img.shields.io/pypi/v/sparkfun_qwiic_serlcd)
![GitHub issues](https://img.shields.io/github/issues/sparkfun/Qwiic_SerLCD_Py)
![License](https://img.shields.io/github/license/sparkfun/Qwiic_SerLCD_Py)
![X](https://img.shields.io/twitter/follow/sparkfun)
![API](https://img.shields.io/badge/API%20Reference-blue?link=https%3A%2F%2Fdocs.sparkfun.com%2Fqwiic_serlcd_py%2Fclassqwiic__serlcd_1_1_qwiic_serlcd.html)

The line of SparkFun Qwiic SerLCD products provide a simple and cost effective solution for adding a "text based" LCD display to your project. Implementing a SparkFun Qwiic interface, a SerLCD is rapidly added to any board that is part of the SparkFun Qwiic ecosystem.

This repository implements a Python package for the SparkFun Qwiic SerLCD series of products. This package works with Python, MicroPython and CircuitPython.

### Contents

* [About](#about-the-package)
* [Getting Started](#getting-started)
* [Installation](#installation)
* [Supported Platforms](#supported-platforms)
* [Documentation](https://docs.sparkfun.com/qwiic_serlcd_py/classqwiic__serlcd_1_1_qwiic_serlcd.html)
* [Examples](#examples)

## About the Package

This python package enables the user to access all of the features of these LCD products via a single Qwiic cable. This includes writing text to the screen, adjusting backlight levels (color), customizing splash screen and much much more. They come pre-programmed with the fully open-sourced [OpenLCD firmware](https://github.com/sparkfun/OpenLCD). All of the capabilities of these LCD screens are each demonstrated in the included examples.


New to qwiic? Take a look at the entire [SparkFun qwiic ecosystem](https://www.sparkfun.com/qwiic).
### Supported SparkFun Products

This Python package supports the following SparkFun qwiic products on Python, MicroPython and Circuit python. 

* [SparkFun SerLCD 16x2 - RGB Backlight (QWIIC)](https://www.sparkfun.com/products/16396)
* [SparkFun SerLCD 16x2 - RGB Text (QWIIC)](https://www.sparkfun.com/products/16397)
* [SparkFun SerLCD 20x2 - RGB Backlight (QWIIC)](https://www.sparkfun.com/products/16398)

### Supported Platforms

| Python | Platform | Boards |
|--|--|--|
| Python | Linux | [Raspberry Pi](https://www.sparkfun.com/raspberry-pi-5-8gb.html) , [NVIDIA Jetson Orin Nano](https://www.sparkfun.com/nvidia-jetson-orin-nano-developer-kit.html) via the [SparkFun Qwiic SHIM](https://www.sparkfun.com/sparkfun-qwiic-shim-for-raspberry-pi.html) |
| MicroPython | Raspberry Pi - RP2, ESP32 | [SparkFun RP2040 Thing+](https://www.sparkfun.com/sparkfun-thing-plus-rp2040.html), [SparkFun RP2350 Thing+](https://www.sparkfun.com/sparkfun-thing-plus-rp2350.html), [SparkFun ESP32 Thing+](https://www.sparkfun.com/sparkfun-thing-plus-esp32-wroom-usb-c.html)
|CircuitPython | Raspberry Pi - RP2, ESP32 | [SparkFun RP2040 Thing+](https://www.sparkfun.com/sparkfun-thing-plus-rp2040.html), [SparkFun RP2350 Thing+](https://www.sparkfun.com/sparkfun-thing-plus-rp2350.html), [SparkFun ESP32 Thing+](https://www.sparkfun.com/sparkfun-thing-plus-esp32-wroom-usb-c.html)

> [!NOTE]
> The listed supported platforms and boards are the primary platform targets tested. It is fully expected that this package will work across a wide variety of Python enabled systems. 

## Installation 

The first step to using this package is installing it on your system. The install method depends on the python platform. The following sections outline installation on Python, MicroPython and CircuitPython.

### Python 

The package is primarily installed using the `pip` command, downloading the package from the Python Index - "PyPi". Note - the below instructions outline installation an Linux-based (Raspberry Pi) system.

#### PyPi Installation

The SparkFun Qwiic SerLCD Python package is part of the overall SparkFun Qwiic Python package which is hosted on PyPi. On systems that support PyPi installation via pip, this library is installed using the following commands

For all users (note: the user must have sudo privileges):
```sh
sudo pip install sparkfun-qwiic
```
For the current user:

```sh
pip install sparkfun-qwiic
```
---
---
> [!CAUTION]
> **TODO** Put together how this works with the new virtual environments used with the latest Python install
---
---
#### Local Installation
To install, make sure the setuptools package is installed on the system.

Direct installation at the command line:
```sh
python setup.py install
```

To build a package for use with pip:
```sh
python setup.py sdist
 ```
A package file is built and placed in a subdirectory called dist. This package file can be installed using pip.
```sh
cd dist
pip install sparkfun_qwiic_serlcd-<version>.tar.gz
```

#### MicroPython Installation
If not already installed, follow the [instructions here](https://docs.micropython.org/en/latest/reference/mpremote.html) to install mpremote on your computer.

Connect a device with MicroPython installed to your computer and then install the package directly to your device with mpremote mip.
```sh
mpremote mip install github:sparkfun/qwiic_serlcd_py
```

#### CircuitPython Installation
If not already installed, follow the [instructions here](https://docs.circuitpython.org/projects/circup/en/latest/#installation) to install CircUp on your computer.

Ensure that you have the latest version of the SparkFun Qwiic CircuitPython bundle. 
```sh
circup bundle-add sparkfun/Qwiic_Py
```

Finally, connect a device with CircuitPython installed to your computer and then install the package directly to your device with circup.
```sh
circup install --py qwiic_serlcd
```

## Getting Started 

## Examples
Below is a quickstart program to print "Hello World!" to the Serial LCD.

See the examples directory for more detailed use examples and [examples/README.md](https://github.com/sparkfun/qwiic_serlcd_py/blob/main/examples/README.md) for a summary of the available examples.

```python
from __future__ import print_function
import qwiic_serlcd
import time
import sys

def runExample():

	print("\nSparkFun Qwiic SerLCD   Example 1\n")
	myLCD = qwiic_serlcd.QwiicSerlcd()

	if myLCD.connected == False:
		print("The Qwiic SerLCD device isn't connected to the system. Please check your connection", \
			file=sys.stderr)
		return

	myLCD.setBacklight(255, 255, 255) # Set backlight to bright white
	myLCD.setContrast(5) # set contrast. Lower to 0 for higher contrast.
	myLCD.clearScreen() # clear the screen - this moves the cursor to the home position as well

	time.sleep(1) # give a sec for system messages to complete
	
	myLCD.print("Hello World!")
	counter = 0
	while True:
		print("counter: %d" % counter)
		myLCD.setCursor(0,1)
		myLCD.print(str(counter))
		counter = counter + 1
		time.sleep(1)

if __name__ == '__main__':
	try:
		runExample()
	except (KeyboardInterrupt, SystemExit) as exErr:
		print("\nEnding Example 1")
		sys.exit(0)
```

