# RTLSDR Scanner - in Python3#

Original Copyright 2012 - 2015 Al Brown

al [at] eartoearoak.com


A cross platform Python frequency scanning GUI for the OsmoSDR rtl-sdr [library](http://sdr.osmocom.org/trac/wiki/rtl-sdr).

Forked from the [Python3 port](https://github.com/yyl-20020115/RTLSDR-Scanner-Python3) of the original as I could not get
it to work for me on Python 3.10 on my Mac.

I have tested on Mac OS Monterey (12.6.1). I had to hand-install OpenGL to get visvis to work (OpenGL deprecated/deleted from later versions of Mac OS).

The exact installation process for OpenGL was a bit ad-hoc, but followed breadcrumbs from [here](https://dev.to/giovannicodes/opengl-setup-in-macos-48cl) and [here](https://www.lukechikkala.com/post/opengl-on-macos).

I tried many things (and eventually got it to work), and it may be as simple as:
* brew install glfw

The other "wisdom" I learned was that I could not run the OpenGL modules in a virtualenv, so I had to work in a global Python context.

When working through firing up the scanner, I then found a succession of aborts which I worked through and fixed. It is largely functional now.

The requirements further down are from the original. Here is what I am working with:
Package | Version
---|---
pip	        |22.2.2
matplotlib	|3.2.1
wxPython	|4.2.0
Pillow	        |9.3.0
pyserial	|3.5
pyrtlsdr	|0.2.93
numpy	        |1.23.4
visvis	        |1.13.0
kiwisolver	|1.4.4
setuptools	|65.4.1
PyOpenGL	|3.1.6

There were a significant set of issues related to later versions of matplotlib to get the list of colormaps. matplotlib 3.2.1 was the latest version that worked with the original code (see get_colours in utils_mpl.py). I have subsequently updated the code to use matplotlib.pyplot.colormaps() which should now work with later versions of matplotlib, but I have not tested yet.


More details can be found [here](http://eartoearoak.com/software/rtlsdr-scanner).

A basic [user manual](https://github.com/EarToEarOak/RTLSDR-Scanner/blob/master/doc/Manual.pdf?raw=true) is also available.

Tested on:

- OS X Monterey (With manual OpenGL install)

## Installation ##
Installation instructions are found [here](http://eartoearoak.com/software/rtlsdr-scanner/rtlsdr-scanner-installation).

Windows executables for x86 and amd64 platforms are available on [GitHub](https://github.com/EarToEarOak/RTLSDR-Scanner/releases).

## Requirements ##

- [Python 2.7.x](http://www.python.org)
- [wxPython](http://www.wxpython.org/)
- [matplotlib](http://matplotlib.org/)
- [numpy](http://www.numpy.org/)
- [Pillow](https://pypi.python.org/pypi/Pillow)
- [rtlsdr](http://sdr.osmocom.org/trac/wiki/rtl-sdr)
- [pyrtlsdr](https://github.com/roger-/pyrtlsdr)
- [pyserial](https://pypi.python.org/pypi/pyserial)

To test for missing libraries run `rtlsdr_scan_diag.py`

Windows 64 bit modules can be found [here](http://www.lfd.uci.edu/~gohlke/pythonlibs/)

## Usage ##

`python -m rtlsdr_scanner [file]`

    file - optional saved scan file to load

**Main Window**

- **Start** - Scan start frequency
- **Stop** - Scan stop frequency
- **Mode** - Single or continuous scanning
- **Dwell** - Sampling time spent on each step
- **FFT Size** - FFT size, greater values result in higher analysis precision (with higher sizes dwell should be increased)
- **Live update** - Update the display on each step (caution only use with small scans and low dwell times)
- **Grid** - Show a grid on the scan

**File Menu**

- **Open...** - Open a saved scan
- **Save As...** - Save a scan
- **Export...** - Export a scan to a CSV file
- **Properties..** - Scan information

**Edit Menu**

- **Preferences** - Set dongle gain, calibration, Local Oscillator and the sample bands to use

**Scan Menu**

- **Start** - Start a scan
- **Stop** - Stop a scan

**Tools Menu**

- **Compare** - Compare two previously saved scans
- **Auto Calibration** - Perform a crude calibration of the dongle to a known signal (this should be a continuous, steady signal)

## License ##

This program is free software: you can redistribute it and/or modify
it under the terms of the GNU General Public License as published by
the Free Software Foundation version 3.

This program is distributed in the hope that it will be useful,
but WITHOUT ANY WARRANTY; without even the implied warranty of
MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
GNU General Public License for more details.

You should have received a copy of the GNU General Public License
along with this program.  If not, see <http://www.gnu.org/licenses/>.
