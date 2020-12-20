## Sensors

### Plant Moisture Sensor
Returns a value between 0 to 1 with 1 being dry.

![sensor-plant-moisture]

### BME280
Using i2c, returns temperature, humidity, and barometric pressure.

![sensor-bme280]

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
- 1x [Centralite 3323-C]
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
- 1x [First Alert ZCOMBO-G] (outside bedroom door)
- 1x [Centralite 3323-C]

#### Remote Functions
Button | Function
--- | ---
On | Turn LIFX bulbs on
Off | Turn LIFX bulbs off
DimUp | Turn outlets on
DimDown | Turn outlets off
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
DimUp | N/A
DimDown | N/A
On (Long) | Start LIFX color swirl
On (Again) | Turn auto timer off

#### Sensor Functions
Value | Function
--- | ---
Luminosity | Enable motion sensor to trigger lights when light levels below a certain threshold
Motion | Trigger lights on with motion
No Motion | Turn lights off after set time

### Porch
- 1x ESP8266 NodeMCUv2
  - 1x BME280 Temp/Humidity/Pressure Sensor
    ESP | Sensor
    --- | ---
    3v3 | VCC
    GND | GND
    D1 | SCL
    D2 | SDA
  - 1x Soil Moisture Sensor
    ESP | Sensor
    --- | ---
    3v3 | VCC
    GND | GND
    A0 | AO
- 1x ESP8266 NodeMCUv2
  - 1x Soil Moisture Sensor
    ESP | Sensor
    --- | ---
    3v3 | VCC
    GND | GND
    A0 | AO
    
[sensor-plant-moisture]: http://www.yourduino.com/sunshop/images/products/large_366_SoilMoisture1-450.jpg
[sensor-bme280]: https://camo.githubusercontent.com/42ffcb8ff3d3625686aef1e1ed29dde44262ea145efb7f4854ce40a438c8cae7/687474703a2f2f692e65626179696d672e636f6d2f696d616765732f672f52576741414f5377492d4257494f42512f732d6c3330302e6a7067
