# Waffle

This keyboard is very similar to the Let's Split and Levinson, the firmware is based on lets_split/rev2.
This firmware is for an Elite-C, Arduino Pro Micro, or other ATmega32u4 based boards.

Hardware files for the keyboard can be found [here](https://github.com/fruzyna/keyboard).

## Build and Install Firmware

Download or clone the `qmk_firmware` repo and navigate to its top level directory.
The easiest way to build and flash firmware is using Docker/Podman.
A utility script is provided to do all the work for you, `util/docker_build.sh`.

```
$ util/docker_build.sh waffle/rev[1/2]:liam
```

## Primary vs Secondary Board

With this version of the firmware, the primary board detects if it is the left or right board.
This is done by checking the level of the F4/GP29 pin.
If it is high, (or often floating) the board is the right board.
If it is low, the board is the left board.
Both boards should be flashed with the exact same image.

## Revisions

The second revision of Waffle transitions from an ATmega32U4 to an RP2040 based microcontroller.
Automatic flashing can be performed on rev1 boards by adding `:flash` to the above command.
Then press the reset button (or bridge RST and GND) to enter DFU mode.
Rev2 boards can be flashed by drag-and-dropping the generated uf2 file (/.build/waffle_rev2_liam.uf2) onto the board's filesystem when in boot mode.