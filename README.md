# Kentec_35_SPI Library

[![Arduino Compile Sketches](https://github.com/Andy4495/Kentec_35_SPI/actions/workflows/arduino-compile-sketches.yml/badge.svg)](https://github.com/Andy4495/Kentec_35_SPI/actions/workflows/arduino-compile-sketches.yml)
[![Check Markdown Links](https://github.com/Andy4495/Kentec_35_SPI/actions/workflows/CheckMarkdownLinks.yml/badge.svg)](https://github.com/Andy4495/Kentec_35_SPI/actions/workflows/CheckMarkdownLinks.yml)

This is a modified version of the [Kentec_35_SPI library][2] included with [Energia][7] and developed by [Rei Vilo][8].

This updated version adds support for the [TM4C129 Connected LaunchPad][5] and addresses a couple specific issues with my [Connected Status Monitor][4] project.

## Changes From Version 1.0.0 Library Included with Energia

1. Add support for TM4C129 LaunchPad:

    To enable the large 12x8 font (font size 3), add the following to `LCD_screen_font.h` at the end of line 48:

   ```cpp
   || defined(__TM4C1294NCPDT__)
   ```

    To select the correct SPI port when connecting the Kentec display to "Booster Pack 1" connectors on the Connected LaunchPad, add the following to `Screen_K35_SPI.cpp`, at the end of line 143:

   ```cpp
   || defined(__TM4C1294NCPDT__)
   ```

2. The library has an issue where the `_getRawTouch()` function can get stuck in an endless loop. File `Screen_K35_SPI.cpp`, has the `_getRawTouch()` function call in the `begin()` method commented out:

   ```cpp
   //    _getRawTouch(x0, y0, z0);
   ```

3. When using the TM4C129 LaunchPad, configure the backlight pin as digital-only instead of PWM. This is to address an issue specific to my setup. In the file `Screen_K35_SPI.cpp`, change the following in the begin() method from:

   ```cpp
   analogWrite(_pinScreenBackLight, 127);
   ```

   To:

   ```cpp
   #if defined(__TM4C1294NCPDT__)
   digitalWrite(_pinScreenBackLight, HIGH);
   #warning Connected LaunchPad platform backlight control
   #else
   analogWrite(_pinScreenBackLight, 127);
   #endif
   ```

## Usage

Other than the changes listed above, this version should work the same as the library included with Energia and should support msp430, msp432, and tiva platforms.

The example program and existing documentation can be used to understand how to use the library.

## References

- Library [documentation][1]
- Web page for [overall library][3] and [special edition for Energia][2]
- [Connected Status Monitor][4]
- TM4C129 Connected Status Monitor [TI product page][5] and [Embedded Computing writeup][6]

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
[100]: https://creativecommons.org/licenses/by-nc-sa/4.0/
[101]: ./LICENSE.txt
[//]: # ([200]: https://github.com/Andy4495/Template-Repo)

[//]: # (This is a way to hack a comment in Markdown. This will not be displayed when rendered.)
