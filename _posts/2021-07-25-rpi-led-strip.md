---
title: Controlling LED Strips via Raspberry Pi
categories:
- Raspberry Pi
---

There are at least two types of LED strips out there. More popular of the two is
made of WS2812 LEDs, which use a single line of control signal.
The other type is based on APA102 LEDs, which require a separate clock signal
apart from data signal thus two lines.

Controlling of WS2812 LED Strips in Raspbery Pi is rather tricky due to the
fact that the signal integrity is critically dependent on the frequency of
the signal. Thankfully, you can use
[Jeremy Garff's code](https://github.com/jgarff/rpi_ws281x) without much difficulty.

Bear in mind though that you need PWM, PCM, or SPI module and you need to set
it to a specific frequency. This means you may not be able to use I2S
(digital audio in/out) if you use PWM or PCM module, or you may need to fix
the core clock of the Raspberry Pi and disable the clock boost feature if
you use SPI interface.
Check the [Limitations section](https://github.com/jgarff/rpi_ws281x#limitations)
for more details.

On the other hand APA102 LED Strips are directly compatible with the standard SPI
interface. Thus you can use any python GPIO libaries that support SPI interface.
This [GitHub discussion](https://github.com/gpiozero/gpiozero/issues/551) can
give you enough information to start with sample codes. A slightly modified
version [can be found here as well.](https://github.com/snowdayclub/rpi-apa102-python)
