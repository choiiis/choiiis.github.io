---
title:  "[Git] remote 명령어로 원격 저장소 연결/삭제/이름 변경하기"
excerpt: "Git 기본 명령어 정리 (3) remote / 로컬 디렉토리를 원격 저장소와 연결하기"

categories:
  - Git
tags:
  - [Git]

permalink: /git/how-to-remote-project/

toc: true
toc_sticky: true
 
date: 2021-12-21
last_modified_at: 2021-12-21
---

로컬의 프로젝트 폴더가 어떤 원격 저장소와 연결되어 있는지 어떻게 확인할 수 있을까?<br>
로컬에 생성한 디렉토리를 원격 저장소와 연결하려면 어떻게 해야할까?<br>
위 고민을 해결해 줄 remote 명령어에 대해서 알아보자.

---

## remote add로 repository와 연결하기

remote_test라는 디렉토리를 balanchew repository에 연결해보려고 한다.

```bash
$ git remote
fatal: not a git repository (or any of the parent directories): .git
```

clone을 했을 때와 동일하게 Git Bash를 실행하고,<br>
`git remote`를 입력하면 git repository가 아니라고 나온다.

그럼 이제 remote_test 디렉토리를 git repository로 만들어보자.

```bash
$ git init
Initialized empty Git repository in D:/--/test/remote_test/.git/
```

이렇게 하면 끝이다.
`git init` 명령은 현재 디렉토리를 git repository로 만들어준다.

```bash
$ ls -a
./  ../  .git/  11111.txt
```

a 옵션을 줘서 숨김 파일까지 다 출력해보면,<br>
이렇게 .git 폴더를 발견할 수 있다. Git Repo가 되었다는 뜻이다.

```bash
$ git remote

```

이 상태에서 git remote를 해보면 아무것도 뜨지 않는다.<br>
당연하다. 아직 연결한 원격 저장소가 없기 때문이다.

```bash
$ git remote add test https://github.com/choiiis/balanchew.git

$ git remote
test
```

`git remote <원격 저장소 이름> <원격 저장소 URL>`를 입력하면 해당 URL 원격 저장소에 내가 설정한 이름으로 연결이 된다.
`git remote`로 'test'라고 설정한 repo와 연결된 것을 알 수 있다!

---

## git remote에 대해서 좀더 알아보자

### 1. 연결된 원격 저장소 확인하기

현재 디렉토리와 연결된 원격 저장소가 어디인지 확인하려면 `remote -v`을 입력하면 된다.

```bash
$ git remote -v
test    https://github.com/choiiis/balanchew.git (fetch)
test    https://github.com/choiiis/balanchew.git (push)
```

위에서 test라는 이름의 원격 저장소로 설정한 balanchew 프로젝트와 연결된 것을 볼 수 있다.

```bash
$ git remote add test2 https://github.com/choiiis/Selfit.git
```

디렉토리를 여러 개의 원격 저장소와 연결하는 것도 가능하다.<br>
Selfit이라는 프로젝트를 test2라는 이름으로 하나 더 연결해보았다.

```bash
$ git remote
test
test2

$ git remote -v
test    https://github.com/choiiis/balanchew.git (fetch)
test    https://github.com/choiiis/balanchew.git (push)
test2   https://github.com/choiiis/Selfit.git (fetch)
test2   https://github.com/choiiis/Selfit.git (push)
```

`git remote`를 입력하면 2개의 원격 저장소에 연결된 것을 확인할 수 있고,<br>
`git remote -v`로 각 원격 저장소가 어떤 프로젝트와 연결되어 있는지 좀더 자세히 알 수 있다.

그리고 이때, `ls`를 입력하면 아무 파일도 존재하지 않는 것을 확인할 수 있다.<br>
즉, `remote`만으로는 저장소에 있는 데이터를 가져오지 못한다.<br>

확실히 remote로 연결하는 것보다는 clone으로 하는 것이 훨씬 편하다. 상황에 따라 다르겠지만, 전체 프로젝트를 통째로 가져오고 싶은 것이라면 그냥 clone을 하는 것이 빠르고 편하다.

<br>

### 2. 원격 저장소 삭제하기

```
$ git remote remove test2

$ git remote
test
```

원격 저장소 삭제 명령은 간단하다.<br>
`git remote remove <저장소 이름>`을 입력하면 된다.

<br>

### 3. 원격 저장소 이름 변경하기

```
$ git remote rename test testtt

$ git remote
testtt

$ git remote -v
testtt  https://github.com/choiiis/balanchew.git (fetch)
testtt  https://github.com/choiiis/balanchew.git (push)
```

원격 저장소 이름을 변경하는 것도 쉽다.<br>
`git remote rename <기존 이름> <변경할 이름>`을 입력하면 원격 저장소 이름이 변경된다.

---

다음 포스팅에서는 협업 프로젝트를 하는 개발자라면 무조건 만나게 될 칭구들...<br>
pull & fetch & merge 삼총사를 다뤄보려고 한다.

<br>

**Reference**<br>
[https://git-scm.com/docs/git-remote](https://git-scm.com/docs/git-remote)