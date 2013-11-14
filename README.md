Rego6xx
=======

This is a simple tool that read sensor values from Rego6xx controlled heat pumps. The Rego controller module can be found in IVT, Bosch and many more brands.
The tool communicates with Rego using RS232, normally trough a RS232-USB converter. You can either build your own cable or buy one. The Rego controller have a serial port which you'll find inside the heat pump.

**NOTE:** The serial interface is TTL +5 volt so you can't conntect directly to a computers serial port. You must have a level converter or you may damage the interface.

Usage
=====
For example, to read outdoor temperature and see alarm state:

```
rego6xx.py --sensor GT2 --sensor alarm
GT2       = 4.6 C
alarm     = OFF
```

To read compressor temperature from another serial port, change label and print it in Graphite style:

```
rego6xx.py --sensor GT6 --map-name GT6,Compressor --graphite --port /dev/ttyUSB1
Compressor 23.7 1384464007
```

If you have a cron job that is executed regulary you could feed the data direct to Graphite with netcat like this:

```
rego6xx.py --sensor GT2 --map-name GT2,house.temp.outdoor --sensor GT3 --map-name GT3,house.temp.hotwater --sensor GT6 --map-name GT6,house.temp.compressor --graphite | nc "graphite.logger.com 2003"
```

Sensors availible
=================

 GT1 - Radiator return 
 GT2 - Outdoor
 GT3 - Hot water (internal tank)
 GT4 - Forward
 GT5 - Room
 GT6 - Compressor
 GT8 - Heat fluid in
 GT9 - Heat fluid out
 GT10 - Cold fluid in
 GT11 - Cold fluid out
 GT3x - Hot water (external tank)
 3kW  - On/off additional heat
 6kW  - On/off additional heat
 P1   - On/off radiator pump
 P2   - On/off Heat carrier pump
 VXV  - On/off Three way valve
 alarm - On/off in alarm state
 heatpower - On/off additional heat

Credit to Jindřich Fučík for reverse engineering the protocol. Many thanks!

More information and inspiration: 
http://rago600.sourceforge.net/

Webshop that sells RS232 interfaces for heat pumps:
http://www.husdata.se/

Graphite:
http://graphite.wikidot.com/

Installation and requirements
=============================
* Python 2.7
* pip install pyserial

Other modules used: datetime, time, logging, argparse

