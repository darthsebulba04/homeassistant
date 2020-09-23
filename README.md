# Home Assistant Configuration

The goal of this setup is to create a home automation system that has no cloud dependancy.  After losing almost all cloud controlled based services over the last year, I decided to DIY all of it and never deal with that again.  There are no hubs or outside controllers in this.  Everything is controlled with a standard install of [Home Assistant] on a Raspberry Pi.

Everything but the [Nest] thermostat is controlled locally and has no online requirement.

Subscribed to [Home Assistant Cloud by Nabu Casa] for location tracking and easy remote access.

If this kind of setup interests you, I wrote up a basic [install] doc for how I accomplished this.
## UI
### iPhone
![hass-iphone-lights] ![hass-iphone-outlets]

![hass-iphone-inside] ![hass-iphone-outside] 

![hass-iphone-batteries]

![hass-iphone-actions]

### iPad
![hass-ipad]

### MacOS
![hass-macos]

## Features

### Away
Critical alerts when away if motion is detected inside. Also turns off all lights and sets thermostat in "eco" mode.

### Backup
Automatically create snapshot each night for backup purposes.

### Do Not Disturb
Ability to manually suppress alerts if I don't want to be disturbed.

### Manual
Manual switches and controls in the event things go wrong.

### Sleep
Internal control for when sleeping, so things don't happen in the middle of the night that aren't supposed to.

### States
Implements [Nonbinary Presence Detection] for easy, yet powerful, presence detection.

State | Purpose
--- | ---
home | In "home" zone or been 'just_arrived' or 'just_woke' for a set amount of time.
just_left | Just left the "home" zone.
away | Been 'just_left' or 'out' for a set amount of time.
just_arrived | Just entered the "home" zone.
in_bed | Bedroom door just closed.
sleeping | Been 'in_bed' for a set amount of time.
just_woke | Bedroom door just opened.
out | Out for a short time. Not fully "away".

````
home -> just_left -> away -> just_arrived -> home

home -> in_bed -> sleeping -> just_woke -> home

home -> out -> away -> just_arrived -> home
````

### YAML
Very little yaml code written.  Ninty percent of all work done was done with the built in configuration editors.

## Hardware
- [Raspberry Pi 4b] w/ 4GB RAM + 32GB SD card
- [Nortek HUSBZB-1] USB Z-Wave+/Zigbee controller
- [HiLetgo 433 Mhz Transmitter + Receiver] Kit
- Various color female-to-female jumper wires
- USB extension cable

![hass-pi]

## Things
### [LIFX A19] 
WiFi based color changing light bulbs.

_Chosen because they're the best color changing bulbs I've seenand they fit in any lamp._
- Count: 4x
- Protocol: wifi

### [Etekcity ZAP] wall outlets
Cheap outlets for controlling basic lamps and salt lamps. 

_Chosen for the independant remote control and low cost._
- Count: 10x
- Protocol: RF 433Mhz

### [Phillips Hue RWL020] Smart Dimmer Switch and Remote
Great remotes for manually toggling lights and changing brightness. 

_Chosen for the many button options and portability._
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

### [Schlage BE469] Touchscreen Deadbolt
Allows keyless entry.

_Chosen because I already had it_
- Count: 1
- Protocol: Z-Wave

### Lowes 1116-S Door Sensor (discontinued)
Open/close sensor. Also reports temperature.

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
- 1x [Etekcity ZAP] (salt lamp night light)

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
DimUp | Enable "out" mode
Off | Disable "away"/"out" mode

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
On (Again) | Turn auto timer off

#### Sensor Functions
Value | Function
--- | ---
Luminosity | Enable motion sensor to trigger lights when light levels below a certain threshold
Motion | Trigger lights on with motion
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
On (Again) | Turn auto timer off

#### Sensor Functions
Value | Function
--- | ---
Luminosity | Enable motion sensor to trigger lights when light levels below a certain threshold
Motion | Trigger lights on with motion
No Motion | Turn lights off after set time

## Integrations

### Home Assistant Community Store (HACS)
For easy install/updating of various community add-ons and frontend enhancements.

#### Battery State Card
Nice card for listing the battery levels of all the sensors.

#### Circadian Lighting
For keeping the color temp on the LIFX bulbs from messing with my sleep.

#### Custom Header
Provides frontend tweaks.

#### iOS Themes - Dark Mode and Light Mode
Slick looking theme that makes [Home Assistant] look like a native application.

#### Weather Card
Cool weather card with animated icons.

### iOS Mobile App
For the location tracking and local/remote control.  Integrates perfectly with [Home Assistant Cloud by Nabu Casa].

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

_Custom add-on created for "sniffing" the on/off codes needed to get this working._

https://github.com/darthsebulba04/hassio-gpio-rf

https://github.com/darthsebulba04/hassio-addons

### Zigbee
For receiving data from the door sensor, simple motion sensor, and phillips hue remotes.

## Future Projects

### BackBlaze
Push daily snapshots to BackBlaze B2 for online backup and recovery.

### Spotify
Integrate Spotify and have music/podcasts play to bluetooth speaker.

[install]: INSTALL.md
[Home Assistant Desktop]: https://github.com/mrvnklm/homeassistant-desktop

[LIFX A19]: https://www.lifx.com/collections/lamps-and-pendants/products/lifx
[Etekcity ZAP]: https://www.etekcity.com/product/100068.html
[Phillips Hue RWL020]: https://www.philips-hue.com/en-us/p/hue-dimmer-switch/046677473372
[ZOOZ ZSE40]: http://www.getzooz.com/zooz-zse40-4-in-1-sensor.html
[Nest]: https://store.google.com/us/product/nest_learning_thermostat_3rd_gen?hl=en-US
[Schlage BE469]: https://www.schlage.com/en/home/faq.html?id=128433

[Home Assistant Cloud by Nabu Casa]: https://www.nabucasa.com
[Home Assistant]: https://www.home-assistant.io
[Nonbinary Presence Detection]: https://philhawthorne.com/making-home-assistants-presence-detection-not-so-binary/
[Raspberry Pi 4b]: https://www.raspberrypi.org/products/raspberry-pi-4-model-b/
[Nortek HUSBZB-1]: https://www.nortekcontrol.com/products/2gig/husbzb-1-gocontrol-quickstick-combo/
[HiLetgo 433 Mhz Transmitter + Receiver]: https://www.instructables.com/id/RF-315433-MHz-Transmitter-receiver-Module-and-Ardu/

[hass-pi]: https://github.com/darthsebulba04/homeassistant/blob/master/rpi-hass.jpg
[hass-ipad]: https://github.com/darthsebulba04/homeassistant/blob/master/hass-ipad.jpg
[hass-iphone-lights]: https://github.com/darthsebulba04/homeassistant/blob/master/hass-iphone-lights.jpg
[hass-iphone-outlets]: https://github.com/darthsebulba04/homeassistant/blob/master/hass-iphone-outlets.jpg
[hass-iphone-inside]: https://github.com/darthsebulba04/homeassistant/blob/master/hass-iphone-inside.jpg
[hass-iphone-outside]: https://github.com/darthsebulba04/homeassistant/blob/master/hass-iphone-outside.jpg
[hass-iphone-batteries]: https://github.com/darthsebulba04/homeassistant/blob/master/hass-iphone-batteries.jpg
[hass-iphone-actions]: https://github.com/darthsebulba04/homeassistant/blob/master/hass-iphone-actions.jpg
[hass-macos]: https://github.com/darthsebulba04/homeassistant/blob/master/hass-macos.jpg
