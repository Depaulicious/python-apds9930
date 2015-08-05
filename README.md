# Python bindings for APDS-9930
Python module for the APDS-9930 I2C Ambient Light and Proximity sensor

This is a Python port of the [AVR APDS-9930 library](https://github.com/Davideddu/APDS9930).

Simple and easy to use. Makes heavy use of Python-specific programming concepts, such as properties, to make usage even easier. Depends on `python-smbus`, the I2C library for Python.

I tested this on Linux a desktop computer, using the I2C pins of a nVidia graphics card, using the Nouveau graphics driver. This has been reported to work for both ATI and nVidia cards, but not for integrated Intel (and I can confirm this).

Check the pinout:

![Graphics-I2C pinout](http://members.dslextreme.com/users/paintyourdragon/img/i2c/port-vga.png)

You may want to read [this article](http://www.paintyourdragon.com/?p=43).

It should work on Raspberry PI.

## Basic usage

**Note:** more detailed usage and documentation coming soon.

Load the `i2c-dev` kernel module.

```
sudo modprobe i2c-dev
```

Install `i2c-tools` to get the `i2cdetect` program, useful to scan for I2C devices.

```
sudo apt-get install i2c-tools
```

List the I2C buses

```
sudo i2cdetect -l
```

Connect the device to the I2C pins, then scan every bus until you find the device. Device should have address 0x39.

```
sudo i2cdetect -y <bus number>

# Sample good output
     0  1  2  3  4  5  6  7  8  9  a  b  c  d  e  f
00:          -- -- -- -- -- -- -- -- -- -- -- -- -- 
10: -- -- -- -- -- -- -- -- -- -- -- -- -- -- -- -- 
20: -- -- -- -- -- -- -- -- -- -- -- -- -- -- -- -- 
30: -- -- -- -- -- -- -- -- -- 39 -- -- -- -- -- -- 
40: -- -- -- -- -- -- -- -- -- -- -- -- -- -- -- -- 
50: -- -- -- -- -- -- -- -- -- -- -- -- -- -- -- -- 
60: -- -- -- -- -- -- -- -- -- -- -- -- -- -- -- -- 
70: -- -- -- -- -- -- -- --
```

Once you have found the correct bus, run Python as root and import the module.

```
sudo python

>>> from apds9930 import APDS9930
```

Open the bus

```
>>> a = APDS9930(bus_number)
```

That's it! Use Python's help function to retrieve the documentation (which is yet to be generated).

```
>>> help(APDS9930)
```