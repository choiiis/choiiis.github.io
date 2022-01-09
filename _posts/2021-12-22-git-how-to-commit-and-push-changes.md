---
title:  "[Git] push 명령어로 local 변경 사항 원격 저장소에 반영하기"
excerpt: "Git 기본 명령어 정리 (4) push : 변경 내역을 원격 저장소에 반영해보자"

categories:
  - Git
tags:
  - [Git]

permalink: /git/how-to-commit-and-push-changes/

toc: true
toc_sticky: true

date: 2021-12-24
last_modified_at: 2021-12-24
---

이전에 Local 변경 사항을 commit 하는 방법까지 다뤘다.  
**Commit 방법을 모른다면 >> [[Git] local 변경 사항 commit하기](https://choiiis.github.io/git/how-to-commit-local-change/)**  

이번 포스팅에서는 commit한 내역을 push하는 방법과,  
commit과 push의 차이에 대해서 알아보자.

---

## git log로 commit 내역 확인

### git log 기본 사용법

먼저 git commit을 한 내역을 확인하려면 `git log` 명령어를 입력하면 된다.

```bash
$ git log
commit f6------17 (HEAD -> master)
Author: choiiis <id@email>
Date:   Wed Dec 22 22:29:36 2021 +0900

    Dec 21 post updated

```

나는 미리 1개의 파일을 변경하여 commit까지 했고,  
이렇게 commit date, author, message까지 확인할 수 있다.

이전 commit 내역까지 다 확인할 수 있으니 참고하세요!

### push하지 않은 commit 목록만 확인하기

```bash
$ git log --branches --not --remotes
```

이렇게 명령어를 입력하면 push하지 않은 commit 목록만 확인할 수도 있다.

---

## git push로 원격 저장소 업데이트

그럼 이제 commit한 내역을 push 해보자.

### git push 기본 사용법

```bash
git push <원격 저장소 이름> <브랜치 이름>
```

이게 push 명령어의 기본 사용법이다.

```bash
$ git push origin master
```

이렇게 입력하면 origin 원격 저장소의 master 브랜치에 변경 내역이 반영되는 것이다.  

### `git push`만 입력해도 된다

```bash
$ git push
```

원격 저장소와 브랜치 이름 없이 입력하면, 현재 브랜치의 원격 저장소로 push된다.  
특정 저장소나 브랜치로 push 하려고 하는게 아니라면 그냥 `git push`만 해줘도 된다.

---

## git commit과 push의 차이

그렇다면 git commit과 push의 차이는 뭘까?  
git commit만으로는 왜 원격 저장소에 반영이 안될까?

우리가 데이터를 변경한 후 commit을 하면 그 내역은 <mark>로컬 저장소</mark>에 반영이 된다.  
즉, 내 pc 내의 저장소에만 반영이 된 것이다.

로컬저장소에 반영된 변경 사항을 원격에도 반영하기 위한 도구가 push다.  
commit한 내역을 push하게 되면, 이제 <mark>원격 저장소</mark>에도 그 내역이 업데이트 되는 것이다.

따라서, commit은 내 pc 내의 작업이 때문에 크게 위험하지 않다.  
하지만 push는 원격 저장소, 즉 공동으로 작업하는 프로젝트에 (개인 프로젝트일 수도 있지만)  
그 내역이 반영되는 것이기 때문에 신중하게 해야한다.

---

크리스마스 이브에 포스팅이라니.. 다들 메리크리스마스임다~
* Reference
[https://git-scm.com/docs/git-push](https://git-scm.com/docs/git-push)
[https://blog.outsider.ne.kr/820](https://blog.outsider.ne.kr/820)
