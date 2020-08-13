# Home Assistant Configuration

The goal of this setup was to create a home automation system that had no cloud dependancy.  After losing almost all services I used over the last year, I decided to DIY all of it and hopefully never have to deal with that again.

Everything but the [Nest] thermostat is controlled locally and has no online requirement.

Subscribed to Home Assistant Cloud by Nabu Casa for location tracking and easy remote access.

## Hardware
- Raspberry Pi 4b w/ 4GB RAM

- HUSBZB-1 USB Z-Wave+/Zigbee controller
- HiLetgo 433M Transmitter + Receiver Kit

- USB extension cable
- Various color female-to-female jumper wires

## Things
### [LIFX A19] 
WiFi based color changing standard light bulbs.

_Chosen because they're the best color changing bulbs I've seen._
- Count: 4x
- Protocol: wifi

### [Etekcity ZAP] wall outlets
Cheap outlets for controlling basic lamps and salt lamps. 

_Chosen for the independant remote control and low cost._
- Count: 10x
- Protocol: RF 433Mhz

### [Phillips Hue RWL020] Smart Dimmer Switch and Remote
Great remotes for manually toggling lights and changing brightness. 

_Chosen for it's many programmable options and portability._
- Count: 3x
- Protocol: Zigbee 

### [ZOOZ ZSE40] 4-in-1 Sensor
Captures motion, temperature, humidity, and luminosity levels.  

_Chosen for all of it's sensor capabilities._
- Count: 2x
- Protocol: Z-Wave+

### [Nest] 3rd Gen Thermostat
Controls the indoor temperature.  

_Chosen for its sleek looks._
- Count: 1
- Protocol: wifi (cloud)

### Lowes 1116-S Door Sensor (discontinued)
Open/close sensor for seeing of bedroom door is open or closed. Also reports temperature.

_Chosen because I already had it_
- Count: 1x
- Protocol: Zigbee

### Lowes 3326-L Motion Sensor (discontinued)
Basic motion sensor. Also reports temperature.

_Chosen because I already had it._
- Count: 1x
- Protocol: Zigbee

## Areas

### Bathroom
- 1x [Etekcity ZAP] (salt lamp nightlight)

### Bedroom
- 2x [Etekcity ZAP] (salt lamp, normal table lamp)
- 1x Lowes 1116-S

### Dining Room
- 1x [Etekcity ZAP] (floor lamp)

### Entry
- 1x [Phillips Hue RWL020]
- 1x Lowes 3326-L
- 1x [Nest]

#### Remote Functions
Button | Function
--- | ---
On | 
Off |

### Kitchen
- 2x [Etekcity ZAP] (salt lamp, night light)

### Living Room
- 2x [Etekcity ZAP] (salt lamp, normal table lamp)
- 2x [LIFX A19] (floor lamp, table lamp)
- 1x [ZOOZ ZSE40]
- 1x [Phillips Hue RWL020]

#### Remote Functions
Button | Function
--- | ---
On | Turn LIFX bulbs on
Off | Turn LIFX bulbs off
DimUp | Increase LIFX brightness
DimDown | Decrease LIFX brightness
On (Long) | Start LIFX color swirl

### Office
- 2x [LIFX A19] (floor lamp, table lamp)
- 1x [ZOOZ ZSE40]
- 1x [Phillips Hue RWL020]

#### Remote Functions
Button | Function
--- | ---
On | Turn LIFX bulbs on
Off | Turn LIFX bulbs off
DimUp | Increase LIFX brightness
DimDown | Decrease LIFX brightness
On (Long) | Start LIFX color swirl

## Integrations

### Circadian Lighting
For keeping the color temp on the LIFX bulbs from messing with my sleep.

### iOS Mobile App (with Nabu Casa Cloud)
For the location tracking and local/remote control.

### LIFX
For control of the LIFX bulbs.

### Met.no
For the weather.

### MQTT
For communication with Open Z-Wave Add-on.

### Nest
For control of the Nest thermostat.

### Open ZWave
For receiving data from the ZOOZ motion sensors.

### Raspberry Pi RF
For sending RF codes to the ZAP outlets.

### Zigbee
For receiving data from the door sensor, simple motion sensor, and phillips hue remotes.

[LIFX A19]: https://www.lifx.com/collections/lamps-and-pendants/products/lifx
[Etekcity ZAP]: https://www.etekcity.com/product/100068.html
[Phillips Hue RWL020]: https://www.philips-hue.com/en-us/p/hue-dimmer-switch/046677473372
[ZOOZ ZSE40]: http://www.getzooz.com/zooz-zse40-4-in-1-sensor.html
[Nest]: https://store.google.com/us/product/nest_learning_thermostat_3rd_gen?hl=en-US
