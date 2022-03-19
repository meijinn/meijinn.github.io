---
layout: post
title:  "Converting Mecha Kame III 2"
date:   2020-05-20
categories: Arduino
tags: Experiment_Class Mid-Term
mathjax: true
author: S.Takahashi
---

* content
{:toc}

I think that how I should do installing two motors, Arduino, and some equipment.

## Arduino
- Using Pro Micro compatible of Arduino
  - Few material savings are desirable, like sensors.

Circuit pictures by adapting Uno [pictures]↓

![img1](/img/0520/1.jpg)


## Circuits requirements
When using Uno R3, circuits are divided from substances at the point of using separated objects. But, Pro Micro has sockets for plugging breadboard, so main bodies and circuits can be the one.





## Mecha KAME main body

The original Mechanical systems consist of these materials, wheeling two tires at same time by using one shaft, two worm gear and two pinion gear, so added a DC motor to control two tires independently and divide shafts in two (break in two).

![img2](/img/0520/2.jpg)

![img3](/img/0520/3.jpg)

For stabilizing wheeling two tires, using fixed small tube are important like cut straw. Scratching for spacing to attach motor, and fixed cable ties, for **9 V** battery space. Making cable for Micro's snap by using Micro USB cable