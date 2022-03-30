---
layout: post
title:  "Bluetooth module rn42xvp-i/rm"
date:   2020-06-10
categories: Graduation_Research
tags: Arduino Prototype
mathjax: true
excerpt: Rn42xvp-i/rm is one of the bluetooth module for prototyping, used by Arduino, Raspberry Pi or something like that.
author: S.Takahashi
---
## Specification

Here are references.
The module pin consists of 1 to 20, "1" pin is the voltage, "10" pin is the ground.
By connecting No.2,3 to Arduino's TX and RX, it can be serial correspondence function into wireless on Bluetooth.
Attention, pin connecting direction is only one-sided.
Pull-down and pull-up resisters are introduced on its using circuits.
Before using Bluetooth communication, Serial communication system used by USB serial port and input by PC keyboard for LED right control is established.

```c
void setup()
{
  pinMode(7,OUTPUT);
  Serial.begin(115200);
  Serial.println("Please Hit any key.");
}

void loop()
{
  if (Serial.available()>0)
  {
    char c = Serial.read();
    if (c == 'w')
    {
      Serial.println("w is pressed.\n");
    }
    if (c == 'a')
    {
      Serial.println("a is pressed.\n");
    }
    if (c == 'o')
    {
      digitalWrite(7,HIGH);
      delay(1000);
      digitalWrite(7,LOW);
    }
  }
}
```
It takes two hours.