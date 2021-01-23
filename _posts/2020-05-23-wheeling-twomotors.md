---
layout: post
title:  "Wheeling Two Motors, and Cooperation of Infrared Remote Controller"
date:   2020-05-23
categories: Arduino Prototype
tags: Experiment_Class
mathjax: true
author: S.Takahashi
---

* content
{:toc}

To analyze infrared signal indicated by Hexadecimal, for allocation of rc motion, moving can show the imagine of prototype electronics.

Infrared Remote Controller [pictures]↓





![img1](/img/0523/1.jpg)

## Behavior Allocation
- VOL+ --- Forward, digitalWrite(HIGH,HIGH)
- Skip --- Turn Right, digitalWrte(LOW,LOW)
- Rewind --- Turn Left, digitalWrite(HIGH,LOW)
- Default --- Stop, digitalWrite(LOW,LOW)

The system consists of NPN transistor, diode, resister discrete.

Two of fundamental circuit [Please refer previous posts], the main components are NPN transistor, Their BASE are connected on Arduino General-Purpose Input Output pin as digital output.