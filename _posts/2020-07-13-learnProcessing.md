---
layout: post
title: Learning Processing Language
date: 2020-07-13
categories: Arduino Processing Prototype July
tags: Graduation_Research Final-Term Term2 Problem
mathjax: false
author: S.Takahashi
---

* content
{:toc}

## What is Processing?
> Processing is a flexible softoware sketchbook and a language for learning how to code within the context of the visual arts. Since 2001, Procesing has promoted software literacy within the visual arts and visual literacy within technology. There are tens of thousands of students, artists, desiginers, researchers, and hobbyists who use Processing for learning and prototyping.

## GameControlPlus API of Processing
Processing has a types of API that allows us to use every gamepad as a PC I/O Interface of USB connection, and then, also has a Serial Connecting API from PC to Arduino of USB protocol, Arduino firmata.

## Sample Trying Processing
I refered [here](https://www.makeuseof.com/tag/arduino-robot-game-controller/),and [here](https://www.youtube.com/watch?v=MUM8_4mWxng).
### First Intraction with Processing is Mouse to Servo
At first, I tried to make servo control program that uses a mouse by reffering youtube, and it works.

the code is [here](https://www.makeuseof.com/tag/arduino-robot-game-controller/).

### Aim to Interact gamepad
Secondary, I have succeed at getting sliders, which is gotton information data of connecting interface something like gamepad.


↓ the code is here
```c
import org.gamecontrolplus.*;

ControlIO control;
ControlDevice device;

ControlButton button;
ControlSlider[] sliders = new ControlSlider[8];

void setup() {
  control = ControlIO.getInstance(this);

  // getting device
  device = control.getDevice("Wireless controller for PLAYSTATION(R)3");
  //device = control.getMatchedDevice("gamepad_config");
  // getting key information
  //button = device.getButton(0);

  // 十字キーを縦横それぞれ取得
  sliders[0] = device.getSlider(0);
  sliders[1] = device.getSlider(1);
  sliders[2] = device.getSlider(2);
  sliders[3] = device.getSlider(3);
  sliders[4] = device.getSlider(4);
  sliders[5] = device.getSlider(5);
  sliders[6] = device.getSlider(6);
  sliders[7] = device.getSlider(7);
}

void draw() {
  //
  //println(button.pressed());

  // key presse 1.0, and release 1.0, other 0.0
  println(sliders[0].getValue());
  println(sliders[1].getValue());
  println(sliders[2].getValue());
  println(sliders[3].getValue());
  println(sliders[4].getValue());
  println(sliders[5].getValue());
  println(sliders[6].getValue());
  println(sliders[7].getValue());
}
```

### Servo control Using gamepad
I aim to implement gamepad controlled servo.
The detail is joystick controlled servo in two directions which consists of 0 to 180 degrees.
But it didn't work.

following next column

↓ the code is here.

```c
import processing.serial.*;

import net.java.games.input.*;
import org.gamecontrolplus.*;
import org.gamecontrolplus.gui.*;

import cc.arduino.*;
import org.firmata.*;

ControlDevice cont;
ControlIO control;

Arduino arduino;

float thumb;

void setup() {
  size(360, 200);
  
  control = ControlIO.getInstance(this);
  cont = control.getMatchedDevice("dfgt");
  
   if (cont == null) {
    println("not today chump");
    System.exit(-1);
  }
  
  //println(Arduino.list());
  arduino = new Arduino(this, Arduino.list()[1], 57600);
  arduino.pinMode(10, Arduino.SERVO);
  
}

public void getUserInput(){
 // assign our float value 
 //access the controller.
 thumb = map(cont.getSlider("servoPos").getValue(), -1, 1, 0, 180);
 //println(thumb);
 
}

void draw(){
 getUserInput();
 background(thumb,100,255);
 
 arduino.servoWrite(10, (int)thumb);
}
```