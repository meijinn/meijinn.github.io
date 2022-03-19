---
layout: post
title:  "Experiment Class 4"
date: 2020-07-24
categories: Arduino
tags: Experiment_Class Mid-Term
mathjax: true
author: S.Takahashi
---

* content
{:toc}

## Implementation for Experiment Making Class Remote Controlled RC Car

Circuit components had problem. Throughout two weeks, system function are separated and any individuals do for installment. Sample circuits was worked but including motor, that wasn't working. They didn't work there be element malfunctions.

## Ultrasonic functions was worked!

Ultrasonic functions was worked, and was able to imply easily and smooth.


## Change policy and goal for completion

At first, Ultrasonic sensor has implied successfully, and other tasks should be done for another function of RC sensitive motion by sound sensor.
Secondary, ultrasonic sensor was needed to update for linear motion.
Finally, sound sensor might have specific limits.

```c
//www.elegoo.com
//2016.12.08
#include "SR04.h"
#define TRIG_PIN 12
#define ECHO_PIN 11
SR04 sr04 = SR04(ECHO_PIN,TRIG_PIN);
long a;
int l=6,r=5;

void setup() {
   Serial.begin(9600);
   pinMode(l,OUTPUT);
   pinMode(r,OUTPUT);
   delay(1000);
}

void loop() {
   a=sr04.Distance();
   Serial.print(a);
   Serial.println("cm");
   delay(1000);

   analogWrite(r,250);
   analogWrite(l,250);
   
   if(a <= 10)
   {
   Serial.println("PAUSE");
   digitalWrite(r,LOW);
   digitalWrite(l,LOW);
   }

   else if(11 <= a <= 15)
   {
    for(int j = 150; j > 100; j--)
    {
      analogWrite(r,j);
      analogWrite(l,j);
      delay(1);
      }
    }

    else if(16 <= a <= 20)
    {
      for(int j = 250; j > 150; j--)
      {
        analogWrite(r,j);
        analogWrite(l,j);
        delay(1);
      }
    }
   
}
```