# Install

The purpose of this document is to provide a good outline for replicating my setup.  

It assumes an understanding of technical systems and a willingness to learn new things.  _This is not a step-by-step document._

I am using a Raspberry Pi 4b, but can use any Pi with the approprate GPIO pins that [Home Assistant] supports.

## Hardware
- [Raspberry Pi 4b] w/ 4GB RAM + 32GB SD card
- [Nortek HUSBZB-1] USB Z-Wave+/Zigbee controller
- [HiLetgo 433 Mhz Transmitter + Receiver] Kit
- Various color female-to-female jumper wires
- USB extension cable

![hass-pi]

## Making Pi
Put together the Raspberry Pi per the documentation, including any heatsinks and fans you received, leaving the top off as you'll need access to the GPIO pins.

Plug the HUSBZB-1 into one of the USB ports.

Leave the SD card out as you'll be needing it later to flash [Home Assistant] on.

### Wiring RF components
Use the below wiring guide to plug in the RF hardware.

The pins on the Pi are numbered and labeled per their specification and can be found in their manual.  The pins on the RF board are numbered left to right.

NOTE: You can use any GPIO pin you want.  I just preferred to keep the cables mostly together for each component.

**Make sure you check the purpose below with the specification.  The wrong power pin can zap the Pi or RF board.**

#### Recv
![rf-recv]

Rpi Pin | RF Pin | Purpose
--- | --- | ---
17 | 1 | 3v3 power
18 | 2 or 3| GPIO 24 (data)
20 | 4 | Ground

### Send
![rf-send]

Rpi Pin | RF Pin | Purpose
--- | --- | ---
11 | 1 | GPIO 17 (data)
02 | 2 | 5v power
09 | 3 | Ground

## Installing Home Assistant
Installing [Home Assistant] is as easy as following their [installation guide].

It's pretty straight forward.

## Installing Add-ons/integrations
The following three add-ons are installed using the supervisor add-on store.

### GPIO RF
This is an add-on I created to get the codes from the RF remote.

You can add the following repository and install the add-on like all others.
https://github.com/darthsebulba04/hassio-addons

The only configuration necessary is to set the GPIO pin in the config and to disable protected mode.

### Z-Wave
This add-on is part of the Official add-ons and is called _OpenZWave_. It requires that you have the _Mosquito broker_ installed and running to use.

Only configuration of the _Mosquito broker_ is to make sure it's ports are open.

Configuration of _OpenZWave_ requires setting the USB port and a network security key.  The add-on documentation is really good and I recommend reading it.

Once these two are running, go to your Configuration > Integrations and add _MQTT_ and _Open ZWave (beta)_.

### Zigbee
Add the _Zigbee Home Automation_ like any other under Configuration > Integrations. It will walk you through setting/detecting the correct serial port.

## Adding devices
This section will outline how to add new devices of each type.

Please note, discovery and pairing of Zigbee and Z-Wave devices sometimes takes a little time.  There are times where a device will add, but not all of it's sensors will be populated (like battery or temperature).  This usually resolves itself after a few minutes.

Have patience during the process and everything should work out fine.  

### RF
Fire up the _GPIO RF_ add-on and point the RF remote at the receiver.  You need to be CLOSE.

You'll see a code and pulselength for each button press in the add-on's log.  I suggest making a spreadsheet to keep track of each button and to do one at a time.  It can get pretty confusing, fast, if you don't.

The next part is where you'll have to write some YAML.  Open up your configuration.yaml (either via SSH or the file editor add-on) and add the following switch.

```
switch:
  - platform: rpi_rf
    gpio: <your gpio pin number>
    switches:
      <name>_1:
        pulselength: <button 1 pulse length>
        code_on: <button 1 on code>
        code_off: <button 1 off code>
```

Add switches for each button you want to program.  Reference the official [rpi_rf integration page] for more details and other options.  

Once all your switches are added, go to your Configuration > Server Controls and verify the config.  If everything checks, restart [Home Assistant] to get your new switches.

### Zigbee
Adding Zigbee devices is probably the easist of the three.  

Go into the _Zigbee Home Automation_ integration configuration and hit the plus in the bottom right corner.  This puts it in discovery mode.

One at a time, put each sensor in pair mode according to the devices instructions.  If you look at the full log, you will be able to see what is going on.

If you don't see anything and you know **for sure** you're putting the device in pair mode correctly, it's probable the sensor isn't supported.

Adding support for a new device is outside the scope of this document. The official site, https://github.com/zigpy/zigpy , is a good starting point if you want to go down that rabbit hole.

### Z-Wave
The _Open ZWave_ add-on has a nice GUI for managing devices.  You can access it from your side menu or the add-on itself.

From the menu, select Open and click Start under the Remote OZWDaemon.  From there, select Add Node and your Z-Wave network is now able to discover new devices.

One at a time, put each sensor in pair mode according to the devices instructions.  You should see messages in log when it starts working.

## What now?
Once you've added all your devices, you can start making all your automations and designing your lovelace ui.  Everyones needs and things are different, so I couldn't even begin to detail what you should do.  

Just have fun with your new non-cloud dependant home automation system. :)

[Home Assistant]: https://www.home-assistant.io/
[installation guide]: https://www.home-assistant.io/getting-started/
[rpi_rf integration page]: https://www.home-assistant.io/integrations/rpi_rf/

[hass-pi]: https://github.com/darthsebulba04/homeassistant/blob/master/rpi-hass.jpg
[rf-send]: https://cdn.instructables.com/ORIG/FU4/UJYA/HM8DG3Q3/FU4UJYAHM8DG3Q3.jpg
[rf-recv]: https://cdn.instructables.com/ORIG/F8T/43EW/HM8DG3Q4/F8T43EWHM8DG3Q4.jpg

[Raspberry Pi 4b]: https://www.raspberrypi.org/products/raspberry-pi-4-model-b/
[Nortek HUSBZB-1]: https://www.nortekcontrol.com/products/2gig/husbzb-1-gocontrol-quickstick-combo/
[HiLetgo 433 Mhz Transmitter + Receiver]: https://www.instructables.com/id/RF-315433-MHz-Transmitter-receiver-Module-and-Ardu/
