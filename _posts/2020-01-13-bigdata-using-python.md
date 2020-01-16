---
layout: post
title: "파이썬을 이용한 빅데이터"
category: post
author: Khyun-kim
description: 파이썬을 이용한 빅데이터에 대하여 공부하며 작성한 내용입니다.
tags: [python]
image: 
---


우리는 데이터를 사용하면서도 생산하고 있다.

가장 흔한 데이터 -> 네비게이션
도로정보, gps,

빅데이터의 특징 3V

Volume (크기)
Variety (다양성)
Velocity (속도)

이 세가지 방면에서 크다

데이터 마이닝
- 데이터 안에서 패턴으로 유효한(의미있는) 무언가를 찾는것
- 사람이 데이터를 보고 판단을 가짐
인공 지능
- 인간과 유사하게 작동하는 컴퓨터
머신 러닝
- 인공 지능을 만들기 위한 기술
딥러닝
- 머신 러닝을 구현하기 위한 기술 중 하나
- 인간의 뉴런을 본 딴 인공 신경망 기술을 활용

Anaconda를 설치할 때 python 실행시 기본으로 Anaconda를 실행하게 하면
Anaconda prompt 가 아닌 Cmd환경에서 python명령으로 Anaconda환경에 진입할 수 있다.
대신 base 가상환경으로 진입하기 위해서는 `activate base` 라는 명령어를 필요로하며
해다 가상환경을 빠져나오기 위해서는 `conda deactivate` 를 입력한다.

python 자료형
리스트
```
 >>> type([1,2,3,4])
 <class 'list'>
```
튜플
```
 >>> type((1,2,3,4))
 <class 'tuple'>
```
집합???
```
 >>> type({1,2,3,4})
 <class 'set'>
```
사전
```
 >>> type({'name' : 'kim', 'height':169})
 <class 'dict'>
```

data와 bigdata 차이
data mining과 머신러닝의 차이