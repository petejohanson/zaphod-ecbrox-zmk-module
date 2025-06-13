# Zaphod ECBrox

This ZMK module contains the shield definition for the [Zaphod ECBrox](https://gitlab.com/lpgalaxy/zaphod-ecbrox) keyboard. Currently, only the XIAO nRF52840 Plus is supported, but it should be possible to support the original XIAO if desired.

## Calibration

The shield includes some default calibration values out-of-the-box, that should work when built with the expected AEBoards Naevy EC switches. Should you need to re-calibration, perform the following steps:

* Flash the firmware that has enabled the `enable_ec_calibrator` snippet. The workflow's been set up to build that firmware by default.
* Once flashed, a CDC ACM "serial port" device should be avaible to your OS.
* Connect to that new port using your serial utility of choice (.e.g PuTTY on windows, or minicom/tio/screen on Linux)
* You'll get a shell prompt like `uart:~$` there.
* At the prompt, type `ec matrix calibration start`
* Make sure not to have any keys of the Zaphod ECBrox pressed. The calibrator will first scan for the "baseline not pressed" values.
* When prompted, you'll then press each key/switch down one after another, in sequence. Be sure to press one at a time, and fully press them quickly to fully depressed for each key.
* Once calibration completes, it should then be able to type properly!
* When you're happy with the calibration, type `ec matrix calibration save` and the calibration data will be saved to flash on the keyboard, and be loaded every future time you plug it in.
* Re-flash with the non-calibration firmware, with whatever full keymap you use.
