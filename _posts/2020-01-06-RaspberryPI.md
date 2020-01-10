---
layout: post
title: "라즈베리파이"
category: post
author: Khyun-kim
description: RaspberryPI를 학습하면서 알게된 내용을 기록한 포스트입니다. RaspberryPI의 기본적인 내용을 담고 있으며, Javascript를 이용하여 학습을 진행하였습니다.
tags: [RaspberryPi, Raspbian, Node.js]
---

# 1. Raspbian  [link](https://www.raspberrypi.org/downloads/raspbian/){:style="font-size:14px;"}
<br><br>
Raspbian은 라즈베리파이를 위해 제작된 리눅스 OS입니다.
<br><br><br><br>
# 2. 라즈베리파이 구조
<br><br>
![HeidiSQL]({{ url }}/assets/img/raspberryPI4.PNG){:style="width:289px;height:222px; float:left;margin-right:20px"}

Raspbian에서 `pinout`명령어를 입력하면 해당 라즈베리파이 버전의 구조를 볼 수 있다.각 모듈의 배치를 확인하여 핀들의 번호를 파악하자. 1이 적혀있는 부분이 1번핀으로 기준점이라고 생각하면 편하다.
<br><br><br><br><br><br><br><br><br><br><br><br>

# 3. 사용되는 javascript library
<br><br>
### 1. node-wiring-pi
<br>
node-wiring-pi 라이브러리는 라즈베리파이의 핀을 이용하여 통신을 할 수 있습니다. `pinMode(PINNUM,INPUT|OUTPUT|PULLUP)`메소드를 통하여 해당 핀의 역할을 정의해야합니다.
정의된 타입에 따라서 `digitalRead(pinNum)` 메소드를 이용해서 특정 핀의 신호를 읽어 올 수 있으며 `digitalWrite(pinNum)`메소드를 사용하여 핀을 통하여 신호를 보낼 수 있습니다.
`setInterval(functionm, time)` 메소드를 이용하여 특정 동작을 특정 시간 마다 반복하도록 설정할 수 있습니다. 해당 라이브러리를 사용하여 PIN에 접근할 때는 wiring pin mapping에 따라야합니다.

<br><br><br><br>
# 4. 실습
<br><br>
## 사용된 모듈
<br>
![sonar]({{url}}/assets/img/sonar.jpg){:style="float:left;margin-right:20px"}


### 초음파 센서 모듈
<br>
Vcc Trig Echo Gnd 핀을 가지고 있으며 Trig 핀을 이용하여 초음파의 송신을 결정하고 
Echo 핀을 통하여 초음파를 송신하고 물체에 부딪혀 반사되는 초음파를 수신하기까지 걸린 시간 출력해주는 모듈입니다.
요구 전압은 5V 입니다.
<br><br><br><br>
### led

<details>
<summary>코드</summary>
<div markdown="1" >
{%highlight javascript%}
var wpi = require(`node-wiring-pi`)
wpi.setup(`wpi`);

var sleep = require(`sleep`)
var micro = require(`microtime`);

var pin =0; // wiring pin mapping
var trig = 4;
var echo =5;

wpi.pinMode(pin,wpi.OUTPUT);
wpi.pinMode(trig,wpi.OUTPUT);
wpi.pinMode(echo,wpi.INPUT);

setInterval(()=>{
    wpi.digitalWrite(trig,wpi.LOW);
    sleep.usleep(2);
    wpi.digitalWrite(trig,wpi.HIGH);
    sleep.usleep(20);
    wpi.digitalWrite(trig,wpi.LOW);

    while(wpi.digitalRead(echo)==wpi.LOW);

    var starttime = micro.now();

    while(wpi.digitalRead(echo)==wpi.HIGH);

    var endtime = micro.now();

    var distance =(endtime-starttime)/58;
    distance= Math.round(distance);
    console.log(`거리는 ${distance} cm 입니다.`);
    if(distance >= 30) {
        wpi.digitalWrite(pin,wpi.LOW);
    }
    else {
        wpi.digitalWrite(pin,wpi.HIGH);
    }
},1000);
{%endhighlight%}
</div>