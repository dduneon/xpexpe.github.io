---
title: 사용하다 알게된 Github 명령어 첫번째 정리
date: 2021-12-07 19:00:00
categories: [Study, GitHub]
tags: [command]
---

*GitHub*를 사용하다가 찾아보면서 알게 된 *GitHub command* 정리!

* * *


#### git pull
- 인수나 옵션 없이 실행하면 현재 로컬에 등록된 추적 중인 브랜치에 해당하는 소스 모두를 가져온다.
- git pull [저장소 주소] [branch] : 저장소 주소에 등록된 최신 소스를 가져와 지정한 브랜치에 저장한다.
- git pull은 git fetch와 git merge가 하는 일을 한번에 수행한다.
- 아무튼 git clone으로 Git에 있는 프로젝트를 처음 불러오고, 그 이후에는 다음 명령어 사용하여 서버에서 받아오는 작업
> git pull origin branchname

- - -

#### branch
- git checkout으로 branch 생성 및 변경 가능
- git branch로 존재하는 branch 리스트를 알 수 있음

- - -

#### After modification
- add -> commit -> push
- 자신의 repository에 수정사항을 반영하는 작업
> git push origin main


- - -


#### Pull request
- push -> github repo 들어오면 **Compare & pull request** 눌러서 PR(Pull Request) 생성


- - -


#### After PR
- 원본 저장소 관리자가 Merge 여부 결정
> Review code -> Merge
> $ git pull (remote)
> $ git branch -d (sub branch)