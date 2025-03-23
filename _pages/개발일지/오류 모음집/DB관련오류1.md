---
title: "AccessDeniedError [SequelizeAccessDeniedError]: Access denied for user ''@'172.17.0.1' (using password: NO)"
tags:
    - Mariadb
    - Sequelize
    - Backend
date: "2025-03-23"
thumbnail: "/assets/img/thumbnail/empty.jpg"
---

Node.js에서 ORM 라이브러리인 Sequlize를 사용하던 중 아래와 같은 오류가 발생하였다!

`AccessDeniedError [SequelizeAccessDeniedError]: Access denied for user ''@'172.17.0.1' (using password: NO)`

해당 오류에 대해 구글링을 해보아도 `using password: YES`에 대한 내용은 많이 검색되나 __NO__ 에 대한 내용은 나오지 않았다.

어렵게 어렵게 드디어 이유를 찾아냈는데 보통 `using password: NO`가 발생하는 원인은 사용자가 DB 비밀번호를 입력하지 않아 발생한다고 한다.

그러나 본인의 경우 아무리 확인을 해봐도 바르게 입력이 되는데 같은 오류로 DB 연결이 되지 않았다.

계속 console.log를 찍어보며 한 단계 한 단계 디버깅을 하던 중

Sequelize의 config.js 파일에 DB에 대한 정보(username, password 등등)를 .env에 저장한 후 불러오는 방식으로 입력하고 있었는데 이 과정이 무슨 이유에서인지 잘 작동되고 있지 않았다.

그러니 당연히 DB에 올바른 정보가 들어가고 있지 않아서 접근이 거부 되었던 것이다!!

일단 급한대로 config.js 파일에 DB에 대한 정보를 직접 하드 코딩하여 입력해 주었더니 해결 되었다!

![DB오류1](/assets/img/error/DB오류1.png)

뭔가 시원찮게 끝났지만 그래도 DB나 Sequelize 모듈에 문제가 있던 것은 아니어서 다행이었다.

다음 포스트에서는 .env 파일 접근이 안되었던 이유에 대해 알아볼 계획이다.

-end-