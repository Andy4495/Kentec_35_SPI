# Kentec_35_SPI Library

[![Arduino Compile Sketches](https://github.com/Andy4495/Kentec_35_SPI/actions/workflows/arduino-compile-sketches.yml/badge.svg)](https://github.com/Andy4495/Kentec_35_SPI/actions/workflows/arduino-compile-sketches.yml)
[![Check Markdown Links](https://github.com/Andy4495/Kentec_35_SPI/actions/workflows/CheckMarkdownLinks.yml/badge.svg)](https://github.com/Andy4495/Kentec_35_SPI/actions/workflows/CheckMarkdownLinks.yml)

This is a modified version of the [Kentec_35_SPI library][2] included with [Energia][7] and developed by [Rei Vilo][8].

This updated version adds support for the [TM4C1294 Connected LaunchPad][5] and addresses a couple specific issues with my [Connected Status Monitor][4] project.

## Changes From Version 1.0.0 Library Included with Energia

### TM4C1294 Connected LaunchPad Specific Changes

1. Add support for 12x8 font (font size 3).

2. Default to standard SPI pins on the BoosterPack 1 connectors (pins 7, 14, 15 on J1/J2). The [tivac platform core][9] has these pins configured as SPI module 2.

3. Use `digitalWrite()` instead of `analogWrite()` for the LCD backlight, since my setup does not use a PWM pin for the backlight.

### Other changes

1. Disable call to `_getRawTouch()`, as it frequently hangs on my setup.

## Usage

Other than the changes listed above, this version should work the same as the library included with Energia and should support msp430, msp432, and tiva platforms.

The included [example program][11] and [documentation][1] can be used to understand how to use the library.

## References

- GitHub [directory][10] containing the source version of the library from the [Tiva board package][9]
- Library [documentation][1]
- Writeups by Rei Vilo for [full version][3] of the library and [special edition for Energia][2]
- [Connected Status Monitor][4] project that uses this library
- TM4C1294 Connected LaunchPad [TI product page][5] and [Embedded Computing writeup][6]

## License

The software and other files in this repository are released under a dual license, depending on the usage:

- For hobbyists and for personal usage:  
  Attribution-NonCommercial-ShareAlike 4.0 Unported ([CC BY-NC-SA 4.0][100])

- For professionals or organisations or for commercial usage:  
  All rights reserved

See the file [`LICENSE.txt`][101] in this repository.

[1]: ./extras/docs/LCD_screen%20-%20Reference%20Manual.pdf
[2]: https://embeddedcomputing.weebly.com/special-edition-for-energia-1610e18.html
[3]: https://embeddedcomputing.weebly.com/lcd_screen-library-suite.html
[4]: https://github.com/Andy4495/ConnectedStatusMonitor
[5]: https://www.ti.com/tool/EK-TM4C1294XL
[6]: https://embeddedcomputing.weebly.com/connected-launchpad-tm4c129-tiva-c-series.html
[7]: https://energia.nu
[8]: https://embeddedcomputing.weebly.com/
[9]: https://github.com/energia/tivac-core
[10]: https://github.com/energia/tivac-core/tree/master/libraries/Kentec_35_SPI
[11]: ./examples/LCD_LifeGame/LCD_LifeGame.ino
[100]: https://creativecommons.org/licenses/by-nc-sa/4.0/
[101]: ./LICENSE.txt
[//]: # ([200]: https://github.com/Andy4495/Template-Repo)

[//]: # (This is a way to hack a comment in Markdown. This will not be displayed when rendered.)
