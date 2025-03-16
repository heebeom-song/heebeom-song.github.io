---
title: "Cloudtype을 활용한 Express 무료 서버 배포하기!"
tags:
    - express
    - server
    - backend
date: "2025-03-16"
thumbnail: "/assets/img/thumbnail/QoddiImg.png"
bookmark: true
---

팀 프로젝트 진행 중 Express로 구현한 backend 서버를 배포해야 하는 상황이 발생했다!

최초에 AWS EC2, RDS 등을 통해 배포하였으나, https 통신을 위해서는 고정 ip를 사용해야 했고 그것은 유료 플랜 이었기에
본인의 안타까운 재정 상황에 따라 무료로 https 배포가 가능한 서비스를 찾아 배포를 시도했다.

그 서비스는 이름하야 **Cloudtype**!

아래 글은 Cloudtype + Express + MariaDB 로 백엔드 서버를 배포하는 방법이다!

# Cloudtype 프로젝트 생성!
---

우선 [Cloudtype](https://cloudtype.io/ko/home)에 접속해서 로그인을 해준다!
로그인은 소셜 로그인을 지원하는데 어차피 배포하려면 github와 연동이 필요하기 때문에 github로 소셜 로그인 해주었다.

그 다음, 프로젝트를 생성해 준다!

![클라우드타입 프로젝트 생성](/assets/img/cloudtypeImg/cloudtype프로젝트생성.png)

# 서비스 추가 하기!
---

프로젝트를 생성했으면 본인이 사용할 서비스를 추가해 준다.

![클라우드타입 프로젝트 생성](/assets/img/cloudtypeImg/서비스추가.png)

본인이 사용할 서비스를 검색하여 클릭해 주면 서비스 설정 탭이 나온다.
나는 MariaDB와 Express(Nodejs)로 서버를 구현했기 때문에 두 서비스를 찾아 추가해 줬다.

우선 MariaDB 설정은 RootPassword, Database Name (더 많은 옵션 클릭시 활성화) 두 내용을 입력해 주고 배포하기를 클릭해준다.

더 많은 옵션을 클릭하면 맨 아래 타임존 또한 설정 가능하다 필요시 설정해 준다.

![클라우드타입 프로젝트 생성](/assets/img/cloudtypeImg/서비스 설정.png)

배포가 완료되면 아래 처럼 서비스가 생성된다.
아래 그림에서 붉은 색 체크 표시가 방금 배포된 Database 주소이며 차후 내가 구현한 express 서버완 연동 시 필요하니 잘 메모해 두자!

![클라우드타입 프로젝트 생성](/assets/img/cloudtypeImg/mariadb설정완료.png)

다음은 nodejs를 추가해주고 필요한 설정을 해준다.

Nodejs를 추가하면 github에 연결을 해줘야한다.
본인이 원하는 레포지토리와 브랜치를 설정해준다.

![클라우드타입 프로젝트 생성](/assets/img/cloudtypeImg/노드깃헙연결.png)

Nodejs 설정에서 본인의 프로젝트에 쓰이는 모든 .env 파일의 내용을 Environment variables에 입력해 준다.
나머지 설정도 본인의 프로젝트에 맞게 작성 후 배포하기를 누른다.

배포가 정상적으로 완료되면 https 통신이 가능한 고정 url로 연결된다.

![클라우드타입 프로젝트 생성](/assets/img/cloudtypeImg/노드연결완료.png)

# 마무리
---

엄청 간단한데 엄청 좋은 기능들을 무료로 이용가능하니 개인이나 소규모 프로젝트를 배포하고자 하는 분들이 애용하셨으면 좋겠다.
node나 mariadb 이외에도 서비스 중인 템플릿이 많으니 아래 공식 문서를 참고해 보자!

👉[Cloudtype 공식 문서](https://docs.cloudtype.io/guide/welcome/intro)

-end-