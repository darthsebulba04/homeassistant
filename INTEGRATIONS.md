# Integrations

## [ESPHome](ESPHOME.md)
For easy programming of, and communication with, the ESP8266 devices and attached sensors.

Check out [ESPHOME.md](ESPHOME.md) for my custom sensors.

## Home Assistant Community Store (HACS)
For easy install/updating of various community add-ons and frontend enhancements.

### Battery State Card
Nice card for listing the battery levels of all the sensors.

### iOS Themes - Dark Mode and Light Mode
Slick looking theme that makes [Home Assistant] look like a native application.

### Multiple Entity Row
Custom card for showing multiple entity values in the same row.  A must have for compact designs.

### RGB Color Card
For the color selection on the lifx light controls.

### Weather Card
Cool weather card with animated icons.

## iOS Mobile App
For the location tracking and local/remote control.  Integrates perfectly with [Home Assistant Cloud by Nabu Casa].

## LIFX
For control of the LIFX bulbs.

## Met.no
For the weather.

## MQTT
For communication with Open Z-Wave Add-on.

## Nest
For control of the Nest thermostat.

## Open Z-Wave
For receiving data from the ZOOZ motion sensors, smoke detector, and deadbolt.

## Raspberry Pi RF
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

## Zigbee
For receiving data from the door sensor, simple motion sensor, and phillips hue remotes.

[Home Assistant Cloud by Nabu Casa]: https://www.nabucasa.com
