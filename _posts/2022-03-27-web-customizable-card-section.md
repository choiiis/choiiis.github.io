---
title:  "input값에 따라 동적으로 grid item 개수 변경하기"
excerpt: "Javascript를 활용해서 카드 섹션 웹페이지 만들기"

categories:
  - Web
tags:
  - [Web, CSS, JS]

permalink: /web/web-customizable-card-section/

toc: true
toc_sticky: true
 
date: 2022-03-24
last_modified_at: 2022-03-24
---

## 카드 섹션 제작 웹페이지 만들기

경기장에서 흔히 볼 수 있는 카드 섹션 응원을 보고 생각한 프로젝트. 컨테이너의 크기나 행, 열의 카드 개수 등을 조절할 수 있고,  
실제 카드 섹션의 색을 변경하여 원하는 디자인을 만들 수 있도록 한다.

---

### input 값에 따라 grid 변경하기

```html
<body>
  <div class="container">
  </div>
  <input type="text">
</body>
```

