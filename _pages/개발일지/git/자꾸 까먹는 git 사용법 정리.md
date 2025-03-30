---
title: "나를 위한 자꾸 까먹는 git 사용법 모음집"
tags:
    - git
    - github
    - 분산 버전 관리 시스템
date: "2025-03-31"
thumbnail: "/assets/img/thumbnail/git,github.png"
---

개발자가 git과 github를 모르는 것은 말도 안되기 때문에 굳이 상세히 설명하진 않겠습니다.

그래도 그냥 넘어가기엔 정 없으니까 간단하게 정리하자면...

### git
- 버전 관리 시스템!
- 파일이나 코드를 버전별로 관리할 수 있어 이전 버전으로 돌아갈 수 도 있고 
- 팀 단위로 파일을 관리할 때 변경 사항을 충돌 없이 병합·관리할 수 있도록 해주는 시스템입니다.

### github
- git으로 버전 관리한 파일을 온라인에 올려서 저장하고 공유할 수 있게 해주는 플랙폼입니다.
- 팀 단위 협업을 용이하게 하고 작업물을 백업할 수 있고 오픈소스 프로젝트할 때 유용합니다.

# 자꾸 까먹는 git 명령어 모음.

## 기본 명령어

- git clone [github repository 주소 이하 원격 저장소 주소] : github 저장소를 로컬환경에 그대로 복사해옴.

- git init : 로컬 프로젝트를 git으로 버전 관리하기 시작!

- git remote add origin [원격 저장소 주소] : github와 연동.

- git add . : 모든 변경 사항 스테이징 영역에 추가, [.]위치에 파일명을 쓰면 해당 파일의 변경 사항만 add 가능.

- git commit -m "[커밋 메세지]" : 현재까지 스테이징 되어 있는 모든 내용을 버전으로 저장.

- git push origin [브랜치명] : 연동되어 있는 github 원격 저장소에 커밋내용 저장.

- git pull origin [브랜치명] : 연동되어 있는 github 원격 저장소의 최신 내용 가져오기.

- git branch : branch 목록 및 현재 위치하고 있는 브랜치 확인.

- git branch [브랜치명] : branch 생성.

- git checkout [브랜치명] : 해당 브랜치로 이동.

- git log : 커밋 기록 확인.

- git reset --hard [커밋id] : 해당 커밋으로 완전히 되돌리기.

- git merge [브랜치명] : 현재 위치하고 있는 브랜치에서 해당 브랜치 합치기.

- git remote -v : 현재 연결되어 있는 저장소 확인.

## Fork 기능 관련 명령어

- git remote add upstream [fork한 저장소 이하 원본 저장소] : upstream 저장소 추가하기.

- git fetch upstream : 원본 저장소의 최신 내용 upstream/main 브랜치를 생성하여 로컬로 가져옴.

- git merge upstream/main : 원본 저장소의 최신 내용을 현재 위치하고 있는 브랜치에 병합.

일단은 여기까지! 이후 계속 추가하겠습니다.

-To be continue-