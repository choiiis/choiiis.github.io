---
title: "GitHub Minimal Mistakes 커스텀 템플릿 업로드"
excerpt: "블로그 커스텀 테마 fork를 위한 repo 생성하기"

categories:
  - GitHub Blog
tags:
  - [GitHub Blog, 깃허브 블로그]

permalink: /github-blog/minimal-mistakes-customized-repo/

toc: true
toc_sticky: true

date: 2022-07-27
last_modified_at: 2022-07-27
---

아주우우 오랜만에 포스팅을 해본다.  
포스팅은 오랜만이지만, 감사하게도 잊을만 하면 한 분씩 댓글도 달아주셔서 간간이 들어왔던 것 같다. 의외로 많은 분들이 이 블로그 테마에 관심을 가져주셔서 fork용 템플릿 형식의 repo를 만들기로 했다.

## 꾸준히 늘어가는 Fork와 Star :3

![star-and-fork](/assets/images/posts_img/github-blog-minimal-mistakes-customized-repo/star-and-fork.png)

그냥 이것저것 바꿔 본 블로그를 생각보다 많은 분들이 좋아해주셔서 놀랐다. 몇 달 동안 꾸준히 Star와 Fork가 늘어가는 걸 보면서 템플릿 형식으로 따로 만들어서 올려놔야지... 했는데 미루고 미루다 드디어 만들어보았다.

사실 템플릿을 만들고 싶었던 또 다른 이유는 내 블로그를 fork 해서 사용하시는 분들의 접근이 내 블로그 통계에 자꾸 반영되기 때문이다ㅜㅜ 방문자 수가 비정상적으로 폭발하거나 내 게시물이 아닌 것들이 구글 analytics에 나타나는 경우도 많았다ㅎㅎ 크게 불편하지는 않았지만 그래도 조금씩 신경 쓰였던 부분이라 겸사겸사 새로 만드는게 좋겠다 싶었다!

---

## Minimal Mistakes customized 레파지토리 업로드

![repo-capture](/assets/images/posts_img/github-blog-minimal-mistakes-customized-repo/repo-capture.png)

블로그 템플릿 repo 업로드 완료!!!  
[https://github.com/choiiis/minimal-mistakes-choiiis-customized](https://github.com/choiiis/minimal-mistakes-choiiis-customized)

생각보다 오래 걸리지 않았다. 너무 오래 전에 세팅한 것들이라 기억이 안나는 부분들도 있어서 구글링 해가면서 만들었다ㅎㅎ 이 블로그 테마를 사용하고 싶다면 위 링크의 repo를 fork 해서 사용하면 된다.

---

## 블로그 repo(choiiis.github.io)와의 차이?

`_config.yml`

```yml
# Site Settings
locale: "ko-KR" #"en-US"
title: "Blog Name Here" # 상단 헤더에 보이는 블로그 타이틀
title_separator: "&#124;"
subtitle: # site tagline that appears below site title in masthead
name: "your name here" # 블로그 닉네임 설정
description: "OOOOO DevLog" # 블로그 설명
url: "https://github-account.github.io" # 블로그 URL
baseurl: # the subpath of your site, e.g. "/blog"
repository: "github-account/github-account.github.io" # GitHub Repo 이름
# logo : # 상단 헤더의 블로그 타이틀 앞에 로고 추가하고 싶을 경우 사용

---
# Site Author (Home에서 해당 내용은 숨김 상태)
author:
  name: "your name here" # 블로그 닉네임
  avatar: "/assets/images/meee.png" # 블로그 프로필 사진
  #   bio              : "hi all!"
  # location         : "Seoul, Korea"
  # email            : "youremailhere@xxxxxx.com"
```

choiiis.github.io와 디자인은 동일하지만, 필요 없는 파일들을 삭제하고 세팅이 필요한 부분들은 초기화 하여 정리해놓았다!

- 개인 별로 세팅해야 하는 부분 초기화 (위 파일 예시)
- 추가 혹은 변경이 필요한 부분들 README.md에 정리
- analytics나 search console등에 반영되는 개인적인 파일들 삭제
- 포스트, 카테고리 목록 등 초기화

---

혹시 수정이 필요한 부분이 있거나 문의 혹은 요청사항이 있으시면,  
댓글 혹은 메일로 연락주세요오 :)
