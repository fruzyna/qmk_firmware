# Keyboard aka LiamBoard I guess

This keyboard is very similar to the Let's Split and Levinson, the firmware is based on lets_split/rev2. This firmware is for an Elite-C, Arduino Pro Micro, or other ATmega32u4 based boards.

Hardware files for the keyboard can be found [here](https://github.com/fruzyna/keyboard).

## First Time Setup

Download or clone the `qmk_firmware` repo and navigate to its top level directory. Then install the [QMK tool](https://beta.docs.qmk.fm/tutorial/newbs_getting_started) and install the dependencies using:

```
$ qmk setup
```

In order to set proper udev rules you may need to run the following:

```
sudo cp /home/liam/workspace/qmk_firmware/util/udev/50-qmk.rules /etc/udev/rules.d/
```

Once your build environment is setup, you'll be able to generate the .hex using:

```
$ make liamboard:liam
```

You will see a lot of output and if everything worked correctly you will see the built hex file, `liamboard_liam.hex`.

If you would like to use one of the alternative keymaps, or create your own, copy one of the existing [keymaps](keymaps/) and run make like so:

```
$ make liamboard:YOUR_KEYMAP_NAME
```

If everything worked correctly you will see a file, `liamboard_YOUR_KEYMAP_NAME.hex`.

For more information on customizing keymaps, take a look at the primary documentation for [Customizing Your Keymap](/docs/faq_keymap.md) in the main README.md.

Finally, to deploy the firmware to the Elite-Cs using DFU mode run:

```
$ make liamboard:liam:dfu
```
