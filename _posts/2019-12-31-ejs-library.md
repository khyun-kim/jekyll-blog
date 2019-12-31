---
layout: post
title: "Node,js 라이브러리들"
author: Khyun-kim
description: Node.js 라이브러리들에 대하여 공부한 내용을 정리하였습니다.
---

## 1. ejs 라이브러리
---
html에 서버 쪽에서 전송하는 데이터를 쉽게 사용할 수 있도록 도와주며 `<script>`태그를 사용하지 않아도 자바스크립트를 중간에 사용할 수 있다.
변수만 사용할 때에는 `<%= 변수이름 %>`의 포맷으로 사용하고 자바스크립트를 사용할 때에는 `<% 자바스크립트 %>`형식으로 사용한다.

```
<% for(var i = 0 ; i < 10 ; i++) { %>
    <h1> <%= data %> </h1>
<% } %>
```

위 코드와 같이 사용하면 `<h1>`태그를 10번 반복해서 삽입하는 것이 가능하다. jekyll에서 사용하는 Django와 유사하다. (Django가 맞는지는 확인해봐야한다.)
<br><br>
## 2. body-parser 라이브러리
---
http를 사용한 연결에서 Request에 포함된 Data를 추출하기 용이하게(파싱하기 편하게) 도와주는 라이브러리이다.
```
var express = require(`express`);
var route = express();

route.get(`/`,(req,res) =>{
    console.log(req.body.[name 태그]);
});
```
위와 같은 방식으로 사용하며 해당 예제는 name 태그를 사용한 예제이다.