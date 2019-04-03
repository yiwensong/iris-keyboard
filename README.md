# iris-keyboard

Stores all the stuff I used to set up my iris keyboard on a chromebook.

## Install Crouton

ChromeOS does not support flashing the hardware. This means we have to install
an OS that actually suports this.
Crostini seemed to not work because it had a difficult time detecting the
hardware.
Crouton had very few issues with the install.

## Install dependencies

I chose to use Ubuntu because that is the distro that I am most familiar with.
Aside from the basic dependencies, you also need to install the packages:

    - arduino
    - gcc-avr

The arduino package is a set of utilities that allow your computer to communicate
with the arduino.
gcc-avr is a package that enables the compilation of our qmk-firmware.

## Create your keymap

https://config.qmk.fm/#/keebio/iris/rev2/LAYOUT

You can create your own keymap using the above link.
You can upload mapping.json to this site to use my settings.

After you finish creating the keymap, hit the compile button and download the
full source. This will be a zip file, so you will need to unzip it.

If you want to use a default or pre-existing keymap, you can skip this step.

## Enable NKRO

Enable the NKRO in the compilation by editing
`qmk_firmware/keyboards/keebio/iris/rules.mk`
and replacing `ENABLE_NKRO = no` to `ENABLE_NKRO = yes`.

## Compile and flash the arduino

In the directory of qmk_firmware (unzipped from the download), run
`sudo make keebio/iris/rev2:<your_keymap_name>:avrdude`.
