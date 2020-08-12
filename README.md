# Home Assistant Configuration

The goal of this setup was to create a home automation system that had no cloud dependancy.  After losing several almost all services I used over the last year, I decided to DIY all of it and hopefully never have to deal with that again.

## Hardware
- Raspberry Pi 4b w/ 4GB RAM
- HUSBZB-1 USB Z-Wave+/Zigbee controller
- HiLetgo 433M Transmitter + Receiver Kit

- USB extension cable
- Various color female-to-female jumper wires

## Sensors
### LIFX color change bulbs
Best color changing bulbs I've seen
- Count: 4x
- Protocol: wifi

### Etekcity ZAP wall outlets
Cheap outlets for controlling basic lamps and salt lamps
- Count: 10x
- Protocol: RF 433Mhz

### Phillips Hue Smart Wireless Dimmer Switch and Remote
Great remotes for manually toggling lights and changing brightness
- Count: 3x
- Protocol: Zigbee 

### ZOOZ 4-in-1 Sensor ZSE40
Captures motion, temperature, humidity, and luminosity levels
- Count: 2x
- Protocol: Z-Wave+

### Lowes 1116-S Door Sensor
For seeing of bedroom door is open or closed
- Count: 1x
- Protocol: Zigbee

### Lowes 3326-L Motion Sensor
Used just because I already had it from before
- Count: 1x
- Protocol: Zigbee
