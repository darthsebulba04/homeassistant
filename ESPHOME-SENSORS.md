# Sensors

## Soil Moisture Sensor
This sensor measures soil moisture levels.  It has two modes:
1. Digital which provides 0 or 1 depending on the moisture level.
2. An analog value between 0 and 1 as a more accurate percentage of the moisture.

![sensor-plant-moisture]

## BME280
Using i2c, this sensor measures temperature, humidity, and barometric pressure.

[Documentation](https://esphome.io/cookbook/bme280_environment.html)

![sensor-bme280]

## TEMT6000
This sensor reads ambiant light levels.  Returns a decimal value between 0 and 1.

[Documentation](https://esphome.io/cookbook/temt6000.html)

![sensor-temt6000]

## PCF8574 Character based display
A simple looking character display.  I'm currently using a 16x2 display to show various temperatures and humidity levels.

[Documentation](https://esphome.io/components/display/lcd_display.html?highlight=display)

![sensor-pcf8574]
    
[sensor-plant-moisture]: http://www.yourduino.com/sunshop/images/products/large_366_SoilMoisture1-450.jpg
[sensor-bme280]: https://esphome.io/_images/bme280-header.jpg
[sensor-temt6000]:https://esphome.io/_images/temt6000-header.jpg
[sensor-pcf8574]:https://esphome.io/_images/lcd-hello_world.jpg
