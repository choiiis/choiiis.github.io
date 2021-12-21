---
title:  "[Git] clone 명령어로 GitHub 프로젝트 로컬에 가져오기"
excerpt: "Git 기본 명령어 정리 (2) clone / 원격 저장소 데이터를 로컬에 가져오는 방법"

categories:
  - Git
tags:
  - [Git]

permalink: /git/how-to-clone-project/

toc: true
toc_sticky: true
 
date: 2021-12-21
last_modified_at: 2021-12-21
---

GitHub에 있는 프로젝트를 로컬에 복제하고 싶다면 clone을 활용하면 된다.<br>
Git의 기본 중의 기본인 clone 방법에 대해서 알아보자.

본 포스트는 Git Bash 기준으로 정리되어 있습니다. GitHub Desktop을 이용한 방법은 아래 링크로!<br>
[GitHub Desktop으로 git 시작하기 - Repository 생성, clone, commit, push](https://choiiis.github.io/git/basics-of-clone-commit-push/)

---

## clone으로 repository 데이터 가져오기

내 GitHub에 있는 프로젝트들 중 하나인 balanchew 프로젝트를 한번 clone 해보겠다.

GitHub에 가서 프로젝트에 들어가보면 이런 화면이 나온다.

<img src="/assets/images/posts_img/git-how-to-clone-and-remote-project/project_capture.png" alt="project_capture" width="70%">

오른쪽 위에 보이는 초록색 "Code" 버튼을 클릭하고,

<img src="/assets/images/posts_img/git-how-to-clone-and-remote-project/url_copy.png" alt="url_copy" width="70%">

사각형 두 개가 겹쳐진 버튼을 클릭하면 URL이 복사된다!

<img src="/assets/images/posts_img/git-how-to-clone-and-remote-project/saved_dir.png" alt="saved_dir" width="70%">

이제 프로젝트를 clone하고 싶은 디렉토리로 이동한다.<br>
나는 test라는 폴더에 이 프로젝트를 clone 해보려고 한다.

<img src="/assets/images/posts_img/git-how-to-clone-and-remote-project/git_bash_here.png" alt="git_bash_here" width="70%">

마우스 오른쪽 버튼 > "Git Bash Here"을 클릭하면 Git Bash 터미널이 나온다.

<img src="/assets/images/posts_img/git-how-to-clone-and-remote-project/git_bash_first.png" alt="git_bash_first" width="70%">

경로가 맞는지 다시 한번 확인을 하고,

```bash
$ git clone https://github.com/choiiis/balanchew.git
```

git clone "URL"을 터미널에 입력한다. Ctrl+V가 안된다면 마우스 오른쪽 버튼 > Paste로 붙여넣자.

```bash
$ git clone https://github.com/choiiis/balanchew.git
Cloning into 'balanchew'...
remote: Enumerating objects: 328, done.
remote: Counting objects: 100% (56/56), done.
remote: Compressing objects: 100% (50/50), done.
remote: Total 328 (delta 26), reused 35 (delta 6), pack-reused 272
Receiving objects: 100% (328/328), 350.86 MiB | 9.54 MiB/s, done.
Resolving deltas: 100% (32/32), done.
Updating files: 100% (286/286), done.
```

clone에 성공했다!

<img src="/assets/images/posts_img/git-how-to-clone-and-remote-project/project_created.png" alt="project_created" width="70%">

"test" 폴더 안에 balanchew 프로젝트 폴더가 생긴 것을 확인할 수 있다. Clone이 완료된 것이다.<br>
폴더에 들어가보면 GitHub에 올라와 있는 폴더/파일들을 모두 로컬로 가져온 것을 확인할 수 있다.

---

## clone과 remote의 차이

>`clone` (동) 복제하다
>
>`remote` (형) 원격의

두 단어의 사전적 정의를 보면 알 수 있듯이,

`clone` : GitHub repository에 있는 내용을 내 로컬(컴퓨터)에 '복제'하는 명령어다. 즉, repository에 있는 파일을 내 로컬의 특정 디렉토리로 가져올 수 있다.

`remote` : Git 홈페이지에 보면 "Manage set of tracked repositories"라고 나와있다. 원격 저장소와의 작업들을 관리하는 명령이다. remote 명령어로 원격 저장소를 연결/확인/변경할 수 있다.

`remote add`와 `clone`의 차이에 대해서 묻는다면,<br>
clone은 remote add를 한 다음 pull(또는 fetch & merge)까지 하는 것이라고 할 수 있겠다.

---

clone과 remote 모두 로컬 디렉토리를 원격 저장소에 연결하지만, 그 방법과 결과가 서로 다르다.<br>
다음엔 git remote를 활용해서 원격 저장소와 연결해보는 방법에 대해 포스팅 해보려고 한다.