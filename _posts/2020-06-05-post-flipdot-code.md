---
title: "Flipdot code"
date: 2020-06-05T20:42:00-00:00
categories:
  - electronics
tags:
  - flipdot
  - processing
  - arduino
  - esp32
---

I've been playing with a 28x7 [Flipdot](https://flipdots.com/en/home/) display I got recently. The goal ultimately is to make a stand alone clock driven by a microprocessor, (Arduino or ESP32), and have it keep in sync over WiFi via NTP. As a proof of concept and a way in to understanding the display, [Processing](https://processing.org) has been a perfect system and language. I've uploaded the code I've written so far to a [github repo](https://github.com/alexdyas/flipdot_fun_processing). Apart from code for a clock display, there are also some other little test routines, bouncing ball, a neat follow the mouse toy, and a very rough graphic equalizer that, frankly needs a lot more work. More technical information in the README.md.

I'll try and upload some video of it working at some point.

More news on the micro-controller driven version as it happens. A shout out to [iizukak](https://create.arduino.cc/projecthub/iizukak) for the [initial idea](https://create.arduino.cc/projecthub/iizukak/flip-dot-clock-3dd850), and also the guys at [AlfaZeta](https://flipdots.com/en/home/) for their help with this very cool mechanical device.
