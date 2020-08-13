# Home Assistant Configuration

The goal of this setup is to create a home automation system that had no cloud dependancy.  After losing almost all services I used over the last year, I decided to DIY all of it and hopefully never have to deal with that again.  There are no hubs or outside controllers in this configuration except for [Home Assistant] itself.

Everything but the [Nest] thermostat is controlled locally and has no online requirement.

Subscribed to [Home Assistant Cloud by Nabu Casa] for location tracking and easy remote access.

## Features

### Away
Alerts when away if motion is detected inside. Also turns off all lights and sets thermostat in "eco" mode.

### Backup
Automatically create snapshot each night for backup purposes.

### Manual
Manual switches and controls in the event things go wrong.

### Sleep
Internal control for when sleeping so things don't happen in the middle of the night that aren't supposed to.

### States
Implements [Nonbinary Presence Detection] for easy, yet powerful, presence detection.

State | Purpose
--- | ---
home | In "home" zone or been 'just_arrived' or 'just_woke' for a set amount of time.
just_left | Just left the "home" zone.
away | Been 'just_left' for a set amount of time.
just_arrived | Just entered the "home" zone.
in_bed | Bedroom door just closed.
sleeping | Been 'in_bed' for a set amount of time.
just_woke | Bedroom door just opened.

````
home -> just_left -> away -> just_arrived -> home

home -> in_bed -> sleeping -> just_woke -> home
````

## Hardware
- Raspberry Pi 4b w/ 4GB RAM
- HUSBZB-1 USB Z-Wave+/Zigbee controller
- HiLetgo 433 Mhz Transmitter + Receiver Kit
- Various color female-to-female jumper wires
- USB extension cable

![hass-pi]

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

_Chosen for it's many button options and portability._
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
On | Enable "away" mode
Off | Disable "away" mode

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

#### Sensor Functions
Value | Function
--- | ---
Luminosity | Enable motion sensor to trigger lights when light levels below a certain threshold
Motion | Trigger lights with motion
No Motion | Turn lights off after set time

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

#### Sensor Functions
Value | Function
--- | ---
Luminosity | Enable motion sensor to trigger lights when light levels below a certain threshold
Motion | Trigger lights with motion
No Motion | Turn lights off after set time

## Integrations

### Circadian Lighting
For keeping the color temp on the LIFX bulbs from messing with my sleep.

### iOS Mobile App
For the location tracking and local/remote control.  Integrates perfectly with [Home Assistant Cloud by Nabu Casa]

### LIFX
For control of the LIFX bulbs.

### Met.no
For the weather.

### MQTT
For communication with Open Z-Wave Add-on.

### Nest
For control of the Nest thermostat.

### Open Z-Wave
For receiving data from the ZOOZ motion sensors.

### Raspberry Pi RF
For sending RF codes to the ZAP outlets.

Pin | Use | Purpose
--- | --- | ---
02 | 5v | Send power (red)
09 | Ground | Send ground (black)
11 | GPIO 17 | Send data (green)
17 | 3v3 | Recv power (red)
18 | GPIO 24 | Recv data (yellow)
20 | Ground | Recv ground (black)

### Zigbee
For receiving data from the door sensor, simple motion sensor, and phillips hue remotes.

## Future Projects

### BackBlaze
Push daily snapshots to BackBlaze B2 for online backup and recovery.

### Spotify
Integrate Spotify and have music/podcasts play to bluetooth speaker.

[LIFX A19]: https://www.lifx.com/collections/lamps-and-pendants/products/lifx
[Etekcity ZAP]: https://www.etekcity.com/product/100068.html
[Phillips Hue RWL020]: https://www.philips-hue.com/en-us/p/hue-dimmer-switch/046677473372
[ZOOZ ZSE40]: http://www.getzooz.com/zooz-zse40-4-in-1-sensor.html
[Nest]: https://store.google.com/us/product/nest_learning_thermostat_3rd_gen?hl=en-US
[Home Assistant Cloud by Nabu Casa]: https://www.nabucasa.com
[Home Assistant]: https://www.home-assistant.io
[Nonbinary Presence Detection]: https://philhawthorne.com/making-home-assistants-presence-detection-not-so-binary/
[hass-pi]: https://github.com/darthsebulba04/homeassistant/blob/master/rpi-hass.jpg
