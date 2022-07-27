---
title: "GitHub Minimal Mistakes 커스텀 템플릿 업로드"
excerpt: " 깃허브 블로그 대공사 여정"

categories:
  - GitHub Blog
tags:
  - [GitHub Blog, 깃허브 블로그]

permalink: /github-blog/minimal-mistakes-customized-repo/

toc: true
toc_sticky: true

date: 2022-07-28
last_modified_at: 2022-07-28
---

아주우우 오랜만에 포스팅을 해본다.  
포스팅은 오랜만이지만, 감사하게도 잊을만 하면 한 분씩 댓글도 달아주셔서 간간이 들어왔던 것 같다.

---

## 뿌듯한 Fork와 Star :3

![star-and-fork](/assets/images/posts_img/github-blog-minimal-mistakes-customized-repo/star-and-fork.png)

마음에 들지 않는 디자인을 참지 못하고 이것저것 바꿔 본 블로그를 생각보다 많은 분들이 좋아해주셔서 놀랐다.  
몇 달 동안 꾸준히 Star와 Fork가 늘어가는 걸 보면서 템플릿 형식으로 따로 만들어서 올려놔야지... 했는데 미루고 미루다 드디어 만들어보았다.

---

## 블로그 repo와의 차이?

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

choiiis.github.io와 디자인은 동일하지만, 필요 없는 파일들을 삭제하고 세팅이 필요한 부분들은 초기화 하여 정리해놓은 것이다.

- 개인 별로 세팅해야 하는 부분 초기화 (위 파일 예시)
- 추가 혹은 변경이 필요한 부분들 README.md에 정리
- analytics나 search console등에 반영되는 개인적인 파일들 삭제
- 포스트, 카테고리 목록 등 초기화

### Minimal Mistakes customized 레파지토리 업로드

![repo-capture](/assets/images/posts_img/github-blog-minimal-mistakes-customized-repo/repo-capture.png)

위에서 언급한 변경 사항들을 반영하여 업로드 완료!!!  
이 블로그를 fork해서 사용하고 싶으신 분들은 [https://github.com/choiiis/minimal-mistakes-choiiis-customized](https://github.com/choiiis/minimal-mistakes-choiiis-customized)에서 fork 해서 사용하시면 됩니다.

---

혹시 수정이 필요한 부분이 있거나 문의 혹은 요청사항이 있으시면,  
댓글 혹은 메일로 연락주세요오 :)
