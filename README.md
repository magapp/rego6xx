Rego6xx
=======

Simple tool that read sensor values from Rego6xx controlled heat pumps. The Rego controller module can be found in IVT, Bosch and many more brands.

This tool communicates with Rego using a RS232 connected cable. The purpose is for reading sensors and temperatures.

Example:

rego6xx --sensor GT2 --sensor alarm

will read the outdoor temperature value and alarm state.

rego6xx --sensor GT1 --graphite --port /dev/ttyUSB1

will read radiator return temperature and display with time stamp, ready to send to Graphite.


Credit to Jindřich Fučík for reverse engineering the protocol. Many thanks!

More information and inspiration: 
http://rago600.sourceforge.net/

Webshop that sells RS232 interfaces for Heat pumps:
http://www.husdata.se/

Graphite:
http://graphite.wikidot.com/

Installation and requirements
=============================
* Python 2.7
* pip install pyserial

Other modules used: datetime, time, logging, argparse
