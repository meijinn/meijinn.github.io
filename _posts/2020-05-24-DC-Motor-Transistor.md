---
layout: post
title:  "DC Motor Control Only Using Transistor"
date:   2020-05-24 09:43:00
categories: Experiment_Class Graduation_Research
tags: Arduino Prototype
mathjax: true
author: S.Takahashi
---

* content
{:toc}

Regarding previous contrains, we can only drive the motor mono-direction. It means not tobe bidirectional control.
We have to some missions about not to use motor drive IC, so the ideal thinking of transistor discrete circuit is needed for project of experiment class.

Because of their some restriction, trying some applied circuits are desirable.

## H-Bridge circuits are got!

To implement H-Bridge Circuits are required two pairs of NPN and PNP transistors numbered-pair.[circuit picture]↓

[H-Bridge Circuit](https://www.marutsu.co.jp/contents/shop/marutsu/mame/64.html)

At first, combining that circuit and coding one motor control are begun, but it just errored by component's malfunction. That also should be expected, they were picked up from outmoded rc toy.

Proceed to implement any other function.

Infrared Remote Controlled car was worked well, so if we can set resister that considerate upper current, the motion are same as bidirection.

The next visions are these.
- I am eager to implement bluetooth module alternative from infrared sensor.
- And then, create system that makes control rc from Dualsohck 3.
- Finally, come true, steering controlled rc car. (this is resemble as Remote Driving System.)
- FPV on it.