---
layout: post
title: "데이터 베이스 공부"
category: post
author: Khyun-kim
description: 데이터 베이스에 대하여 공부한 내용을 기록한 포스트입니다.<br>현재 기록된 내용은 MySQL과 MongoDB가 있습니다.
tags: [MySQL, MongoDB]
---

# MySQL

## 1. 사용하면 좋은 툴

>HeidiSQL

![HeidiSQL]({{ url }}/assets/img/heidisql.png_l){:style="width:125px;height:125px;"}

HeidiSQL 직관적인 UI
<br><br><br>

## 2. SQL문
<br>

>사용시 주의점<br>
HeidiSQL과 같은 데이터 베이스 관리 프로그램이 아닌 프로그램에서 사용할 때 먼저 인증 과정을 거쳐야한다.
```
ALTER USER 'root'@'localhost' IDENTIFIED WITH mysql_native_password BY '1234'
```
위 명령어를 사용하면 정상적인 쿼리 이용이 가능하다.

<br><br>

>SHOW DATABASES

작성된 데이터베이스들을 조회한다.<br>
```
> SHOW DATABASES;
+--------------------+
| Database           |
+--------------------+
| test               |
+--------------------+
```

<br>
<br>

> CREATE DATABASE [name] [options]

특정 이름을 가진 데이터베이스를 부여된 옵션에 맞추어 생성한다.

# [MongoDB](https://www.mongodb.com/)

MongoDB는 통신 규격을 JSON을 사용하는 NoSQL 데이터베이스이며 RDMS에 비해 데이터를 빠르게 처리할 수 있으며, 데이터 분산에 용이하다.
이 때문에 빅데이터 분야에서는 NoSQL 계열을 많이 사용한다고 한다.

