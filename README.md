# Robo Flavored OctoPrint Firmware Updater

This plugin can be used to flash the firmware of your printer by selecting a file or an URL.  After flashing your Mainboard (ATMEGA256o based), it is recommended you reset your EEPROM using `M502` to restore defaults and save with an `M500`.  

It can also check automatically for new firmwares by getting the printer's current firmware version and checking online
for the latest one.

![Firmware Updater Plugin](http://i.imgur.com/3S37KUM.png)

The automatic firmware update is done by detecting the current firmware version from the M115's response. This response string is
parsed to identify the MACHINE_TYPE and the FIRMWARE_VERSION. This information is then sent to a web service which responds with
information about the latests firmware available and the URL to download it, which is done automatically after the check.

The update check can be done automatically after connecting to the printer or manually from the plugin's dialog.

## Installing on Robo C2 and R2

Install via the bundled [Plugin Manager](https://github.com/foosel/OctoPrint/wiki/Plugin:-Plugin-Manager)
or manually using this URL:

    https://github.com/Robo3D/OctoPrint-FirmwareUpdater/archive/master.zip

## For all other Raspbian distributions you may need the following dependencies

### AVRDUDE setup

AVRDUDE needs to be installed in the server, where OctoPrint is running.

#### Raspberry Pi

```
sudo apt-get update
sudo apt-get install avrdude
```

#### Ubuntu (12.04 - 14.04 - 15.04)

Information about the package needed can be found here [Ubuntu avrdude package](https://launchpad.net/ubuntu/+source/avrdude)

```
sudo add-apt-repository ppa:pmjdebruijn/avrdude-release
sudo apt-get update
sudo apt-get install avrdude
```

## Configuration

In order to be able to flash firmwares, we need to install avrdude and then specify it's path. The path to avrdude can be set in the plugin's configuration dialog.
This can be usually found in `/usr/bin/avrdude`

In order to change the URL where the updates are checked you will need to edit OctoPrint's config.yaml.
