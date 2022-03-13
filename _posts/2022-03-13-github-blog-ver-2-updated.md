---
title: "GitHub 블로그 2.1 ver 업데이트 완료 : 무엇이 달라졌나"
excerpt: " 깃허브 블로그 대공사 여정"

categories:
  - GitHub Blog
tags:
  - [GitHub Blog, 깃허브 블로그]

permalink: /github-blog/ver-2-updated/

toc: true
toc_sticky: true
 
date: 2022-03-13
last_modified_at: 2022-03-13
---

![merge-command](/assets/images/posts_img/github-blog-ver-2-updated/merge_cmd.png)

블로그 디자인을 싹 바꿨다. 폰트가 마음에 안 들어서 시작한 작업인데 생각보다 수정하고 싶은 부분들이 많았다. 어디를 어떻게 바꿨는지 한번 정리해봤다!


## Pretendard 폰트로 변경

▶ Before

![ver1_post.png](/assets/images/posts_img/github-blog-ver-2-updated/ver1_post.png)

▶ After

![ver2_post.png](/assets/images/posts_img/github-blog-ver-2-updated/ver2_post.png)

기능적인 부분보다는 디자인적인 부분을 많이 수정했다. 먼저 RIDI 바탕체 폰트를 사용하고 있었는데, 가독성에는 바탕체보다 고딕체가 좋다는 글을 보고 바꿔야지 생각을 했다. 전자책의 서체라 특별히 가독성이 떨어질 것 같지는 않았는데, 폰트 자체가 살짝 두꺼워서 그런지 막상 고딕체로 바꾸고 보니 훨씬 깔끔하고 눈에 잘 들어왔다.

변경한 폰트는 Pretendard다. Windows에서 Mac의 폰트를 느끼고 싶다? 라면 최선의 선택이 아닐까 싶다. 어느 날 폰트에 꽂혀서 블로그에 정말 한 30가지 쯤의 폰트를 적용해봤는데, 이보다 깔끔한 건 없었다. 훨씬 깔끔하게 보이는 것 같아서 아주 만족스럽다. 참고로 영어 폰트는 Montserrat이다. Pretendard의 영어 폰트 느낌이 조금 아쉬워서 Pretendard와 잘 어우러지면서도 깔끔한 폰트를 선택했다.

## 메인 페이지 수정 사항

▶ Before

![ver1_main](/assets/images/posts_img/github-blog-ver-2-updated/ver1_main.png)

▶ After

![ver2_main](/assets/images/posts_img/github-blog-ver-2-updated/ver2_main.png)

### 메인 컬러 변경 & 카테고리 정리

메인 컬러를 연두색에서 주황색으로 변경했다. 새로 바꾼 폰트와 색상이 안 어울리는 느낌도 있었고, 주황색이 창의적이고 혁신적인 인상을 주는 색상이라고 해서 과감하게 바꿔봤다.

카테고리도 싹 정리했다. 괜히 너무 세세하게 나눠 놓은 느낌도 들고, 카테고리를 정하거나 추가할 때마다 어디에 넣어야 하지 고민을 하게 되어서 심플하게 바꿨다. 스크롤 하지 않아도 전체 카테고리를 볼 수도 있고, 너무 세분화되어 있지 않아서 선택하기에도 좋다.

### Author 소개 파트 About 페이지로 따로 생성

![ver2_about](/assets/images/posts_img/github-blog-ver-2-updated/ver2_about.png)

메인 페이지에서 계속 보이는 나의 소개란도 지웠다. 공간을 꽤 많이 차지하기도 했고, 포스트에 좀더 집중하도록 하기 위해서 없앴다. 대신 따로 About 페이지를 추가해서 간단한 소개를 작성했다.

<img src="/assets/images/posts_img/github-blog-ver-2-updated/ver2_logo.png" width="50%" height="50%" alt="ver2_logo" />

메인 페이지에 소개 파트를 완전히 지워버리니 조금 허전하기도 하고 내 블로그임을 나타낼 만한 것이 헤더의 블로그 이름뿐이라 아쉬웠다. 그래서 비루한 그림 실력으로 심플한 나만의 로고를 만들어서 추가했다.

### Categories 페이지 삭제

![ver1_categories](/assets/images/posts_img/github-blog-ver-2-updated/ver1_categories.png)

이전 버전에는 Navigation에 "Categories"를 클릭하면 카테고리 별로 게시글을 모아서 보는 페이지가 있었다. 메인 페이지에 카테고리 기능을 만들어 놓았는데, 굳이 페이지까지 있어야 할 필요가 없는 것 같아서 삭제했다.

### Comments 기능 추가

![ver2_comments](/assets/images/posts_img/github-blog-ver-2-updated/ver2_comments.png)

마지막으로 댓글 기능을 추가했다. 검색을 해보니 Disqus는 광고도 있고 무겁다는 글이 많아서, 깔끔하고 GitHub 사용자면 누구나 작성할 수 있는 Utterances를 골랐다.

---

기존 블로그는 꽉 차보이는 면에서 좋기도 했지만, 구조나 폰트 등이 어수선해서 집중력이 떨어지는 느낌이었다. 그래서 이번 업데이트는 정리와 삭제에 좀더 집중했는데, 원하던 느낌을 잘 살린 것 같아서 만족스럽다!