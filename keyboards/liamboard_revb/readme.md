# Keyboard aka LiamBoard I guess

This keyboard is very similar to the Let's Split and Levinson, the firmware is based on lets_split/rev2.
This firmware is for an Elite-C, Arduino Pro Micro, or other ATmega32u4 based boards.

Hardware files for the keyboard can be found [here](https://github.com/fruzyna/keyboard).

## Build and Install Firmware

Download or clone the `qmk_firmware` repo and navigate to its top level directory.
The easiest way to build and flash firmware is using Docker/Podman.
A utility script is provided to do all the work for you, `util/docker_build.sh`.

```
$ sudo util/docker_build.sh liamboard_revb/rev2:liam
```

Then press the reset button (or bridge RST and GND) to enter DFU mode.

## Primary vs Secondary Board

With this version of the firmware, the primary board detects if it is the left or right board.
This is done by checking the level of the F4 pin.
If it is high, (or often floating) the board is the right board.
If it is low, the board is the left board.
Both boards should be flashed with the exact same image.
