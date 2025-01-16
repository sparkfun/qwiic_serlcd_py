![Qwiic SerLCD Python Module](docs/images/gh-banner-py-qwiic-serlcd.png "qwiic SerLCD Python Module" )

# SparkFun Qwiic SerLCD - Python Module

![PyPi Version](https://img.shields.io/pypi/v/sparkfun_qwiic_serlcd)
![GitHub issues](https://img.shields.io/github/issues/sparkfun/Qwiic_SerLCD_Py)
![License](https://img.shields.io/github/license/sparkfun/Qwiic_SerLCD_Py)
![X](https://img.shields.io/twitter/follow/sparkfun)

The line of SparkFun Qwiic SerLCD products provide a simple and cost effective solution for adding a "text based" LCD display to your project. Implementing a SparkFun Qwiic interface, a SerLCD is rapidly added to any board that is part of the SparkFun Qwiic ecosystem.

This repository implements a Python module for the SparkFun Qwiic SerLCD series of products. This module works with Python, MicroPython and CircuitPython.

### Contents

* [About](#about-the-module)
* [Getting Started](#getting-started)
* [Installation](#installation)
* [Supported Platforms](#supported-platforms)
* [Documentation](https://docs.sparkfun.com/Qwiic_SerLCD_Py/)
* [Examples](#examples)

## About the Module

This python module enables the user to access all of the features of these LCD products via a single Qwiic cable. This includes writing text to the screen, adjusting backlight levels (color), customizing splash screen and much much more. They come pre-programmed with the fully open-sourced [OpenLCD firmware](https://github.com/sparkfun/OpenLCD). All of the capabilities of these LCD screens are each demonstrated in the included examples.


New to qwiic? Take a look at the entire [SparkFun qwiic ecosystem](https://www.sparkfun.com/qwiic).
### Supported SparkFun Products

This Python module supports the following SparkFun qwiic products on Python, MicroPython and Circuit python. 

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
> The listed supported platforms and boards are the primary platform targets tested. It is fully expected that this module will work across a wide variety of Python enabled systems. 


---
---
---
## Getting Started

### Installation


### PyPi Installation
This repository is hosted on PyPi as the [sparkfun-qwiic-serlcd](https://pypi.org/project/sparkfun-qwiic-serlcd/) package. On systems that support PyPi installation via pip, this library is installed using the following commands

For all users (note: the user must have sudo privileges):
```sh
sudo pip install sparkfun-qwiic-serlcd
```
For the current user:

```sh
pip install sparkfun-qwiic-serlcd
```

### Local Installation
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

## Examples


See the examples directory for more detailed use examples.

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

