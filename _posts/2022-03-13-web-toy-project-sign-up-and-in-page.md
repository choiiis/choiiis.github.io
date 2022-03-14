---
title:  "회원가입 페이지 구현하기 : 이메일 도메인 드롭다운"
excerpt: "HTML, CSS, VanillaJS 토이 프로젝트 : input 내부에 버튼 넣기, 커스텀 drop down 구현하기"

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

이번 토이 프로젝트에서는 웹페이지의 기본적인 기능인 회원가입, 로그인을 구현해보려고 한다. 자바스크립트도 조금 익숙해져 가고 있어서 회원가입, 로그인 페이지 정도는 구현할 수 있을 것 같았다. ID 중복 확인, 유효성 검사 등 퍼블리싱만 하던 프로젝트보다는 좀더 신경써야 할 부분이 많았다. 서버쪽도 간단하게 구현해서 실제 데이터 송수신까지 진행해보려고 한다. 


## UI 디자인, 설계

![project-sketch](/assets/images/posts_img/web-toy-project-sign-up-and-in-page/project-sketch.png)

구글에 회원가입 페이지를 검색해서 나오는 여러 화면들을 참고해서 만들어봤다.

![check-list](/assets/images/posts_img/web-toy-project-sign-up-and-in-page/check-list.png)

엑셀에 대략적으로 체크 리스트를 작성해서 정리했다. 어떤 부분을 신경써야 할지 미리 정리를 하고 구현해야 중요한 부분들을 잊지 않고 개발할 수 있다.

## 개발 기록

구현이 어려웠던 부분이나 기록하고 싶은 부분 정리

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


### 도메인 리스트 Drop-down 구현

![email-input](/assets/images/posts_img/web-toy-project-sign-up-and-in-page/email-input.png)

#### 클릭 시 드롭다운 보이기

```html
<div class="box domain">
  <div class="domain__selected">직접 입력</div>
  <ul class="domain__list">
    <li class="option">naver.com</li>
    <li class="option">google.com</li>
    ...
  </ul>
</div>
```
자바스크립트를 통해 domain 클래스 클릭 시 domain__list에 active 클래스를 추가하는 방식으로 구현했다. 

```css
.domain .domain__list {
  overflow: hidden;
  max-height: 0;
}

.domain .domain__list.active {
  top: 100%;
  left: 0;
  overflow-x : hidden;
  overflow-y : auto;
  max-height: 60px;
}
```

active 클래스가 추가되면 드롭다운이 보이도록 구현했다. 추가되기 이전에는 overflow를 hidden, max-height를 0으로 설정해서 보이지 않게 했다. 그리고 추가된 이후에는 max-height를 설정해서 드롭다운 박스의 높이를 정했다. 그리고 overflow-y를 auto로 설정해서 내용이 보이게 했다.

```javascript
const domainEl = document.querySelector('.domain')
const domainListEl = document.querySelector('.domain__list')

let isActiveDomainList = false
domainEl.addEventListener('click', function () {
  isActiveDomainList = !isActiveDomainList // transition
  if(isActiveDomainList) {
    // active domain list
    domainListEl.classList.add('active')
  } else {
    // hide domain list
    domainListEl.classList.remove('active')
  }
});
```

isActiveDomainList를 변수를 두어 domain 클래스를 클릭할 때마다 boolean 값이 반전되도록 했다. isActiveDomainList가 false, 즉 domain 리스트가 보이지 않는 상태이면 active 클래스를 추가한다. active 클래스를 추가하면 드롭다운 리스트가 보이게 된다.