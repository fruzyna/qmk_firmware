# Waffle

This keyboard is very similar to the Let's Split and Levinson, the firmware is based on lets_split/rev2.
Schematics and PCB design files for the keyboard can be found [here](https://github.com/fruzyna/waffle).

## Microcontroller Support

This keyboard was originally designed for use with the [Elite-C](https://keeb.io/products/elite-c-low-profile-version-usb-c-pro-micro-replacement-atmega32u4) an ATmega32U4 board.
However, it now also supports the [Elite-Pi](https://keeb.io/products/elite-pi-usb-c-pro-micro-replacement-rp2040) which uses an RP2040.
Both boards and other compatible boards (like the Pro Micro) are currently supported.

## Build Firmware

Download or clone the `qmk_firmware` repo and navigate to its top level directory.
The easiest way to build and flash firmware is using Docker/Podman.
A utility script is provided to do all the work for you, `util/docker_build.sh`.

```
$ util/docker_build.sh waffle/[atmega32u4/rp2040]:default
```

## Flash Firmware

The Elite-C can be flashed by running the `docker_build.sh` script with an additional `:flash` flag.
When building is complete, press the reset button to trigger flashing.

The Elite-Pi can be flashed by holding the boot button when connecting to USB.
Then drag and drop the firmware image (`.build/waffle_rp2040_default.u2f`) to the virtual filesystem.

## Primary vs Secondary Board

With this version of the firmware, the primary board detects if it is the left or right board.
This is done by checking the level of the F4/GP29 pin.
If it is high, (or often floating) the board is the right board.
If it is low, the board is the left board.
Both boards should be flashed with the exact same image.
