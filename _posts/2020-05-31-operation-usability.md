---
layout: post
title:  "For updating operation usability"
date:   2020-05-31
categories: Arduino Prototype
tags: Graduation_Research Experiment_Class
mathjax: true
author: S.Takahashi
---

* content
{:toc}

- Adding Infrared sensor allocated button for smooth works.
- More quickly.

The project first section is completed.

Having done:
- Linear motion are implemented by DC Motor Driver.




[codes here]↓

```c
#include <Arduino.h>
#include <IRremote.h>
#include "SR04.h"

#define A 0xFF629D //16736925 forward
#define B 0xFF22DD //left 
#define C 0xFFC23D //right
#define D 0xFF02FD //pause
#define E 0xFFA25D //lf
#define f 0xFFE21D //lr
int l=6,r=5;
int receiver = 3;
unsigned long RED;
//plusultrasonic
#define TRIG_PIN 12
#define ECHO_PIN 11
SR04 sr04(ECHO_PIN,TRIG_PIN);
long a;//plusultrasonic

IRrecv irrecv(receiver);     // create instance of 'irrecv'
decode_results results;      // create instance of 'decode_results'

void _mForward()
{ 
      Serial.println("VOL+ forward.");
      for (int i = 100; i < 250; i++)
      {
        analogWrite(r,i);
        analogWrite(l,i);
        delay(10);
      }
}
void _mleft()
{
      Serial.println("FAST FORWARD left.");
        analogWrite(r,250);
        analogWrite(l,0);
}
void _mright()
{
      Serial.println("FAST FORWARD right.");
       analogWrite(r,0);
       analogWrite(l,250);
}
void _mfleft()
{
      for (int i = 250; i > 50; i--)
      {
        analogWrite(r,250);
        analogWrite(l,i);
        delay(1);
      }
      delay(400);
      for (int i2 = 50; i2 < 250; i2++)
      {
        analogWrite(r,250);
        analogWrite(l,i2);
        delay(1);
      }     
}

void _mfright()
{
      for (int i = 250; i > 50; i--)
      {
        analogWrite(r,i);
        analogWrite(l,250);
        delay(1);
      }
      delay(400);
      for (int i2 = 50; i2 < 250; i2++)
      {
        analogWrite(r,i2);
        analogWrite(l,250);
        delay(1);
      }     
}
void _mStop()
{
      Serial.println("PAUSE");
      digitalWrite(r,LOW);
      digitalWrite(l,LOW);
}
void _mstepStop()
{
      delay(250);
      _mStop();
}

void setup() {
  //---set pin direction
  pinMode(l,OUTPUT);
  pinMode(r,OUTPUT);
  Serial.begin(9600);
  _mStop();
  irrecv.enableIRIn(); // Start the receiver
}

void loop() {
  //---back and forth example
   a=sr04.Distance();
   Serial.print(a);
   Serial.println("cm");
   if(a <= 10)
    {
    Serial.println("PAUSE");
    digitalWrite(r,LOW);
    digitalWrite(l,LOW);
    }
    //delay(1000);
  if (irrecv.decode(&results)) // have we received an IR signal?
  {
    RED=results.value;
    Serial.println(RED); 
    irrecv.resume(); // receive the next value
    delay(150);

    if (RED==A)
    {
      _mForward();
      //_mstepStop();
    }
    else if (RED==B)
    {
      _mleft();
      _mstepStop();
    }
    else if (RED==C)
    {
      _mright();
      _mstepStop();
    }
    else if (RED==D)
    {
      _mStop();
    }
    else if (RED==E)
    {
      _mfleft();
      //delay(400);
      //_mForward();
      //_mstepStop();
    }
    else if (RED==f)
    {
      _mfright();
      //delay(400);
      //_mForward();
      //_mstepStop();
    }
  }
}
```

For future:
- The second section of Infrared Sensor RC car project will have completed and transferring to develop Bluetooth RC car idea operating from Android Smartphone, and coding modification.