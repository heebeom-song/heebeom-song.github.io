---
title: "Github page을 활용한 개인 블로그 만들기!"
tags:
    - user manual
    - 블로그 만들기
date: "2024-10-12"
thumbnail: "/assets/img/thumbnail/블로그사진.png"
bookmark: true
---

개발자라면 응당 하나 쯤은 갖고 있을 개발 블로그를 만들기 위해 어떤 플랫폼이 좋을 지 검색해 보던 와중에 "github page"를 이용해 직접 개인 블로그를 손쉽게 만들 수 있다는 정보를 발견했다!

아래 글은 누군가 말들어 놓은 블로그 템플릿(jekyll theme)과 github page를 활용하여 개인 블로그를 만드는 내용이다.

# Github Page 생성하기!
---
github page는 github에서 제공해 주는 무료 호스팅 서비스로 github repository에 웹 문서를 만드는데 필요한 파일을 업로드하여 손쉽게 웹페이지를 만들 수 있다.

1. github 계정에 호스팅할 때 사용할 repository 생성!

github page로 웹페이지를 호스팅하면 https://[username].github.io 와 같은 주소 형식을 가진다.
그렇기 때문에 호스팅 할 때 사용할 repository의 이름은 [username].github.io로 설정한다.
만약 그렇게 하지 않으면 오류가 날 수 있으니 반드시 이름을 맞춰주도록 하자!
공개 여부는 public으로 설정한다.

![블로그만들기_레포이름](/assets/img/블로그만들기_레포이름.png)

2. github page 설정.

생성한 repository로 이동 -> 상단 settings 탭 클릭 -> 좌측 pages 탭 클릭 -> 브랜치 설정 후 Save!

![블로그만들기_github설정](/assets/img/블로그만들기_page설정.png)

설정을 완료하면 https://[username].github.io 주소로 페이지가 만들어진다. 설정 반영까지 5 ~ 10분 정도 소요되니 바로 접속되지 않는다고 걱정하지 말자!

# Ruby와 Jekyll 설치하기!
---
github page를 만들었으면 이제 그 페이지를 블로그로 만드는 작업이 남았다!
github page를 이용해 블로그를 만들기 위해서는 Jekyll과 Ruby가 꼭 필요하다.

여기서 잠깐! 그해서 Jekyll은 뭐고 Ruby는 뭔데? 라는 의문을 품을 수도 있을 것 같아 짧게 설명한다.
Jekyll은 Github 공동 설립자인 톰 프레스턴 워너가 만든 정적 사이트 생성기로 마크업 언어로 글을 작성하면 미리 정의해 놓은 규칙에 따라 정적인 웹 사이트를 만들어준다.
Ruby는 Jekyll을 개발할 때 사용한 프로그래밍 언어이다.

1. Ruby 설치 하기
https://rubyinstaller.org/downloads/

ruby 인스톨러 사이트에 접속하여 본인의 컴퓨터 운영체제에 맞는 버전을 다운로드 받는다.
본인은 64비트 윈도우 운영체제를 사용하고 있어 아래 사진과 같은 버전을 다운로드 하였다.

![루비설치](/assets/img/루비설치.png)

다운로드가 완료되면 `Start Command Prompt with Ruby`가 설치 되었을 것이다. 찾아서 실행 시키면 cmd 창이 하나 뜬다.
그 cmd 창에서 앞서 생성한 github page의 repository 로컬 파일로 이동한 후 `chcp 65001` 명령어를 입력 하여 인코딩해준다.

![루비cmd](/assets/img/루비cmd.png)

2. Jekyll 설치
앞서 열어놓은 ruby prompt에 아래 명령어를 순서대로 입력하여 Jekyll을 설치해 준다.

```
$ gem install jekyll bundler
$ gem install webrick
```

설치가 되면 아래 명령어로 jekyll 프로젝트를 생성해 준다.

```
$ jekyll new ./
```

여기서 아래와 같은 오류가 발생할 수 있는데 이는 프로젝트를 생성할 위치가 비워져있지 않아서 발생하는 오류이다.
이때는 고민하지말고 --force 명령어로 강제 생성 시켜주면 해결된다.

![jekyll 오류](/assets/img/지킬%20오류.png)
![jekyll오류해결](/assets/img/지킬오류해결.png)

이제 아래 명령어를 통해 각종 번들 파일 다운과 jekyll 서버를 구동해 보자.

```
$ bundle install
$ bundle exec jekyll serve
```

위 명령어 입력 후 localhost:4000 으로 접속하면 github page로 만들어 놓은 웹 페이지가 뜰 것이다!

# Jekyll Theme 적용하기!
---

구글에 jekyll theme 이라고 검색해 보면 다른 훌륭하신 분들이 만들어 놓은 블로그 테마가 많이 나온다.
그 중 본인이 맘에 드는 테마를 선택하여 사용하면 된다.

본인은 https://jekyll-themes.com/byanko55/jekyll-theme-satellite 이 테마를 선택하였다.
선택 이유는...
1. 댓글 기능이 구현되어 있어 방문자와 소통 가능.
2. 블로그 내 검색 기능 구현되어 있어 쉽게 탐색 가능.
3. 카테고리를 커스터마이징 하기 편하게 구현 되어 있음.
4. 액티브한 화면이 마음에 들었음.

아무튼 각자 본인의 마음에 드는 테마를 선택하여 해당 테마의 github에 접속, 모든 소스코드를 복사한 후 앞서 생성한 github page 로컬 파일에 붙여넣어준다.
그 후 ruby prompt에서 `bundle install` 명령어를 입력하면...!

An error occurred while installing wdm (0.1.1), and Bundler cannot continue. 라는 오류가 발생한다...
이것은 앞거 복붙한 소스코드 중 gemfile의 `gem "wdm", "~> 0.1.1", :platforms => [:mingw, :x64_mingw, :mswin]` 부분 때문인데 이 부분은 없애버려도 무방하기 때문에 주석 처리 후 다시 `bundle install`를 입력하면...!

![테마설치성공](/assets/img/테마설치성공.png)

성공한다!

마지막으로 `bundle exec jekyll serve` 명령어를 입력하여 localhost:4000에 정상적으로 해당 테마가 렌더링되는지 확인한다!

![블로그](/assets/img/thumbnail/블로그사진.png)

# Github Page에 Push!
---

이제 마지막으로 로컬에 있는 블로그 테마 소스코드를 Github page가 설정되어 있는 repository로 push하여 https://[username].github.io 주소로도 접속 가능하게끔 해줄 것이다.

git bash나 vscode로 터미널을 열어 github page 로컬 파일이 있는 위치로 가서 아래 명령어로 github에 push해 주면된다.

```
$ git add *
$ git commit -m "커밋 메세지"
$ git push origin master(or main)
```

github의 해당 repository로 이동해 잘 push 되었나 확인 후 https://[username].github.io 주소로 접속해 보면 해당 블로그 테마가 잘 렌더링 되는 것을 확인해 볼 수 있을 것이다!
적용까지 5 ~ 10분 걸리니 기다렸다 접속해 보자!

# 마무리...
---

이제 블로그 틀은 다 갖춘셈이다!
본인이 선택한 jekyll theme 사이트에서 글을 post하는 방법이나 커스터마이징하는 방법을 찾아보고 그에 맞게 블로그를 운영해 나가면 된다.

현재 서비스되고 있는 블로그 서비스들(velog, tistory..)에 비해 다소 불편한 점이 있긴하다.

예를 들면 글 하나 post하려 해도 블로그 서비스들은 포스트하기 버튼 눌러서 글쓰고 저장하면 그만이지만 github page 블로그는 vscode 열어서~ 마크다운 파일 만들어서~ 마크다운으로 열심히 글쓰고~ 저장하고~ github에 push하고~ 등등 해야한다...

하지만 본인이 원하는 기능을 커스터마이징하고 이것저것 꾸밀 수 있는 점은 좋은 것 같다. 
그리고 개발자가 본인이 만든 웹페이지 하나 쯤 있는 것도 믓찐일이 아니겠는가?! 흐흐

각종 질문이나 의견은 댓글로 남겨주시면 감사하겠습니다!
-end-