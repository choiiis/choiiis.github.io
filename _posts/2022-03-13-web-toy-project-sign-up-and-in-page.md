---
title:  "VanillaJS로 회원가입 페이지 구현하기"
excerpt: "HTML, CSS에 Javascript 연습을 곁들인 토이 프로젝트"

categories:
  - Web
tags:
  - [Web, CSS]

permalink: /web/toy-project-sign-up-and-in-page/

toc: true
toc_sticky: true
 
date: 2022-03-13
last_modified_at: 2022-03-13
---


## 회원가입 페이지 구현

웹페이지의 기본적인 기능인 회원가입, 로그인을 구현해보려고 한다. 자바스크립트도 조금 익숙해져 가고 있어서 회원가입, 로그인 페이지 정도는 구현할 수 있을 것 같았다. ID 중복 확인, 유효성 검사 등 퍼블리싱만 하던 프로젝트보다는 좀더 신경써야 할 부분이 많았다. 서버쪽도 간단하게 구현해서 실제 데이터 송수신까지 진행해보려고 한다. 


## UI 디자인, 설계

![project-sketch](/assets/images/posts_img/web-toy-project-sign-up-and-in-page/project-sketch.png)

구글에 회원가입 페이지를 검색해서 나오는 여러 화면들을 참고해서 만들어봤다.

*기획 excel 캡쳐 추가*

## 개발 기록

### input 안에 button 넣기

![input-button-before](/assets/images/posts_img/web-toy-project-sign-up-and-in-page/input-button-before.png)

input 태그 안에 아이디 중복 확인 버튼을 넣으려고 한다. 먼저, input과 button을 감싸는 div 태그를 하나 추가했다. 부모 div의 position을 relative, 자식인 button의 position을 absolute로 설정하고 부모의 오른쪽에서 조금 떨어진 곳에 위치하기 위해 right 값을 설정했다.

```html
<div id="info__id">
  <input type="text" placeholder="아이디 입력(6~20자)"/>
  <button>중복 확인</button>
</div>
```

```css
.info #info__id {
  position: relative;
}

#info__id button {
  position: absolute;
  top: 0;
  bottom: 0;
  right: 5px;
  margin: auto 0;
}
```

![input-button-after](/assets/images/posts_img/web-toy-project-sign-up-and-in-page/input-button-after.png)
