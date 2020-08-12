# Home Assistant Configuration

The goal of this setup was to create a home automation system that had no cloud dependancy.  After losing several almost all services I used over the last year, I decided to DIY all of it and hopefully never have to deal with that again.

## Hardware
- Raspberry Pi 4b w/ 4GB RAM
- HUSBZB-1 USB Z-Wave+/Zigbee controller
- HiLetgo 433M Transmitter + Receiver Kit

- USB extension cable
- Various color female-to-female jumper wires

## Sensors/outlets
### [LIFX A19] color change bulbs
Chosen because they're the best color changing bulbs I've seen.
- Count: 4x
- Protocol: wifi

### [Etekcity ZAP] wall outlets
Cheap outlets for controlling basic lamps and salt lamps. Chosen for the independant remote control.
- Count: 10x
- Protocol: RF 433Mhz

### [Phillips Hue Smart Dimmer Switch and Remote]
Great remotes for manually toggling lights and changing brightness. Chosen for it's many programmable options and portability.
- Count: 3x
- Protocol: Zigbee 

### [ZOOZ ZSE40] 4-in-1 Sensor
Captures motion, temperature, humidity, and luminosity levels.  Chosen for all of it's sensor capabilities.
- Count: 2x
- Protocol: Z-Wave+

### Lowes 1116-S Door Sensor (discontinued)
For seeing of bedroom door is open or closed
- Count: 1x
- Protocol: Zigbee

### Lowes 3326-L Motion Sensor (discontinued)
Used just because I already had it from before
- Count: 1x
- Protocol: Zigbee

## Rooms

### Bathroom
- 1x [Etekcity ZAP] (salt lamp nightlight)

### Bedroom
- 2x [Etekcity ZAP] (salt lamp, normal table lamp)
- 1x Lowes 1116-S

### Dining Room
- 1x [Etekcity ZAP] (floor lamp)

### Entry
- 1x [Phillips Hue Smart Dimmer Switch and Remote]
- 1x Lowes 3326-L

### Kitchen
- 2x [Etekcity ZAP] (salt lamp, night light)

### Living Room
- 2x [Etekcity ZAP] (salt lamp, normal table lamp)
- 2x [LIFX A19] (floor lamp, table lamp)
- 1x [ZOOZ ZSE40]
- 1x [Phillips Hue Smart Dimmer Switch and Remote]

### Office
- 2x [LIFX A19] (floor lamp, table lamp)
- 1x [ZOOZ ZSE40]
- 1x [Phillips Hue Smart Dimmer Switch and Remote]

[LIFX A19]: https://www.lifx.com/collections/lamps-and-pendants/products/lifx
[lifx-pic]: https://cdn.shopify.com/s/files/1/0219/0638/products/PDP_Hero_-_Product_hero_1800x1800.jpg?v=1591079434
[Etekcity ZAP]: https://www.etekcity.com/product/100068.html
[zap-pic]: https://external-content.duckduckgo.com/iu/?u=http%3A%2F%2Fecx.images-amazon.com%2Fimages%2FI%2F416Sv6j7KTL._SY300_.jpg&f=1&nofb=1
[Phillips Hue Smart Dimmer Switch and Remote]: https://www.philips-hue.com/en-us/p/hue-dimmer-switch/046677473372
[phillips-pic]: https://www.assets.signify.com/is/image/PhilipsLighting/b95c17641bc945adb714a9b900a25f2f?wid=1280&hei=1280&$jpglarge$
[ZOOZ ZSE40]: http://www.getzooz.com/zooz-zse40-4-in-1-sensor.html
[zooz-pic]: https://www.getzooz.com/assets/img/other/06-ZOOZ-4-IN-1-SENSOR-REQUESTED-FEATURES.png
