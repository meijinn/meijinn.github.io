---
layout: post
title:  "Using ArduinoISP for Solving Problem that Pro Micro was Probably Broken by High Voltage"
date:   2020-06-08
categories: Arduino Prototype
tags: Experiment_Class
mathjax: true
author: S.Takahashi
---

* content
{:toc}

Experiment class is in tandem with graduation research. When I'd been getting of adding sensors for controlling function by ultrasonic sensor, the problem was happened caused by incorrect wiring. Pro Micro was missed on PC serial port because of its hardware trouble.

## Fixing

Pushing reset pin is one of the solver. But it was not effective, nothing was getting well. I thought that it has an another trouble, like software's one.

## Rewriting Bootloader from Another Arduino by Using ArduinoISP

Pro Micro is compatible with Arduino Leonardo, not UNO, a little complexed. Wiring like these.





| Arduino UNO | Pro Micro | Signal line |
|-------------|-----------|-------------|
| D13         | 15        | SCK         |
| D12         | 14        | MISO        |
| D11         | 16        | MOSI        |
| D10         | RST       | RESET       |
| 5 V         | VCC       |             |
| GND         | GND       |             |

1. Connect USB cable UNO to PC, and Start Arduino IDE, don't connect Pro Micro ON USB
2. Select "Tools" → "Board" → "Arduino".
3. "File"　→ "Sketch"　→ "Example" → "11. ArduinoISP"
4. "ArduinoISP" and writing "ArduinoISP" code to UNO makes it as AVR  ISP
5. "Tools" → "Board" → "Arduino Leonardo"
6. "Tools"　→ "Writing board" → "Arduino as ISP"
7. "Tools" → "Writing bootloader" → Run it, 
8. Check Pro Micro recognition on PC, by connecting USB cable removing UNO and Pro micro is recognized PC as Arduino Leonardo.