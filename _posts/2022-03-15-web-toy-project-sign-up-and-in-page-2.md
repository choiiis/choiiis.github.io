---
title:  "회원가입 페이지 구현하기 : select로 이메일과 생년월일 입력"
excerpt: "HTML, CSS, VanillaJS 토이 프로젝트 : select 태그, option 동적 생성, 생년월일 유효성 검사까지"

categories:
  - Web
tags:
  - [Web, CSS, VanillaJS]

permalink: /web/toy-project-sign-up-and-in-page-2/

toc: true
toc_sticky: true
 
date: 2022-03-15
last_modified_at: 2022-03-15
---

지난 포스트에서 드롭다운을 div, ul, li를 활용하여 HTML, CSS만 구현을 했는데, 이를 select로 변경하기로 했다. option쪽 디자인을 조금 포기해야 했지만, 모바일에서 option 선택이 편리하고, "선택을 한다"는 목적에 맞는 태그라는 점에서 수정을 택했다. 그리고 가장 큰 이유는 네이버 회원가입 페이지를 참고해보니 select로 되어 있었기 때문이다.

---

## 개발 기록 이어가기

구현이 어려웠던 부분이나 기록하고 싶은 부분 정리

### 이메일 도메인 select box 구현

#### select, option 태그로 이메일 도메인 선택하기

![email-domain-select](/assets/images/posts_img/web-toy-project-sign-up-and-in-page-2/email-domain-select.png)

```html
<input class="box" id="domain-txt" type="text"/>
<select class="box" id="domain-list">
  <option value="naver.com">naver.com</option>
  <option value="google.com">google.com</option>
  <option value="hanmail.net">hanmail.net</option>
  <option value="nate.com">nate.com</option>
  <option value="kakao.com">kakao.com</option>
</select>
```

select 태그 내부에 option 태그를 넣어 선택할 목록을 추가했다. 

```css
select.box {
  width: 100%;
  height: 50px;
  box-sizing: border-box;
  margin-left: 5px;
  padding: 5px 0 5px 10px;
  border-radius: 4px;
  border: 1px solid #d9d6d6;
  color: #383838;
  background-color: #ffffff;
  font-family: 'Montserrat', 'Pretendard', sans-serif;
}

option {
  font-size: 16px;
}

.info .box#domain-list option {
  font-size: 14px;
  background-color: #ffffff;
}
```

css도 간단하다. 기본 폰트나 background 색상 설정이 별로라 그 부분만 수정을 해주었다. select, option 태그를 사용하는 것의 단점은 커스텀에 한계가 있다는 점이다. option에 hover 했을 때 파란색 배경색 등의 변경이 불가능하다.

---

#### "직접 입력" 선택 시 input 활성화 하기

![email-select-text](/assets/images/posts_img/web-toy-project-sign-up-and-in-page-2/email-select-text.png)

직접 입력 선택 시 : input창 활성화

![email-select-naver](/assets/images/posts_img/web-toy-project-sign-up-and-in-page-2/email-select-naver.png)

도메인 option 선택 시 : input창에 도메인 입력 & 비활성화

```html
<select class="box" id="domain-list">
  <option value="type">직접 입력</option>
  <option value="naver.com">naver.com</option>
  ...
</select>  
```

먼저 "직접 입력" option을 추가하여 default로 설정했다. 이때 #domain-list input에 도메인을 입력할 수 있다.

```javascript
// 도메인 직접 입력 or domain option 선택
const domainListEl = document.querySelector('#domain-list')
const domainInputEl = document.querySelector('#domain-txt')
// select 옵션 변경 시
domainListEl.addEventListener('change', (event) => {
  // option에 있는 도메인 선택 시
  if(event.target.value !== "type") {
    // 선택한 도메인을 input에 입력하고 disabled
    domainInputEl.value = event.target.value
    domainInputEl.disabled = true
  } else { // 직접 입력 시
    // input 내용 초기화 & 입력 가능하도록 변경
    domainInputEl.value = ""
    domainInputEl.disabled = false
  }
})
```

![email-domain-select](/assets/images/posts_img/web-toy-project-sign-up-and-in-page-2/email-domain-select.gif)

(화면 녹화를 하면 select box가 보이지 않는다)  
#domain-list 중 "직접 입력" 이외의 값이 선택되면 도메인을 입력할 수 있는 #domain-txt input 요소에 도메인이 입력되고 비활성화 된다. 그리고 "직접 입력"을 선택할 경우 disabled를 false로 변경하고 입력된 도메인을 초기화한다.

---

### 생년월일 셀렉트 박스 구현

#### 생년월일 select option을 동적으로 생성하기

![birth-select-flex](/assets/images/posts_img/web-toy-project-sign-up-and-in-page-2/birth-select-flex.png)

```html
<div class="info" id="info__birth">
  <select class="box" id="birth-year">
    <option disabled selected>출생 연도</option>
  </select>
  <select class="box" id="birth-month">
    <option disabled selected>월</option>
  </select>
  <select class="box" id="birth-day">
    <option disabled selected>일</option>
  </select>
</div>
```

select 태그 안에 default로 세팅될 값들만 옵션으로 넣어놓았다. disabled 속성으로 placeholder의 역할을 하는 해당 값들은 선택되지 않도록 했고, disabled된 속성을 보이게 하기 위해 selected 속성을 추가했다.

```css
/* SECTION - BIRTH */
.info#info__birth {
  display: flex;
}

.info#info__birth select {
  margin-left : 7px;
}

.info#info__birth select:first-child {
  margin-left : 0px;
}
```

CSS는 year, month, day 3개의 select 박스를 flex를 사용하여 수평으로 배치한 것 이외에는 특별한 것은 없다. 셀렉트 박스의 디자인은 이메일 셀렉트 박스와 동일하기 때문에 위의 select.box 태그를 참고하면 된다.

```css
.info#info__birth select::-webkit-scrollbar {
  width: 10px;
}

.info#info__birth select::-webkit-scrollbar-thumb {
  background-color: #b6b6b6;
  border-radius: 3px;
}

.info#info__birth select::-webkit-scrollbar-track {
  background-color: #ebe9e9;
  border-radius: 6px;
}
```

참고로 위와 같이 설정하면 select의 스크롤 바 커스텀도 가능하다!

```javascript
// '출생 연도' 셀렉트 박스 option 목록 동적 생성
const birthYearEl = document.querySelector('#birth-year')
// option 목록 생성 여부 확인
isYearOptionExisted = false;
birthYearEl.addEventListener('focus', function () {
  // year 목록 생성되지 않았을 때 (최초 클릭 시)
  if(!isYearOptionExisted) {
    isYearOptionExisted = true
    for(var i = 1940; i <= 2022; i++) {
      // option element 생성
      const YearOption = document.createElement('option')
      YearOption.setAttribute('value', i)
      YearOption.innerText = i
      // birthYearEl의 자식 요소로 추가
      this.appendChild(YearOption);
    }
  }
});
// Month, Day도 동일한 방식으로 구현
```

여기까지 구현을 하면 아래와 같이 셀렉트 박스의 목록이 잘 나타난다.

![birth-select-list](/assets/images/posts_img/web-toy-project-sign-up-and-in-page-2/birth-select-list.png)

JS 소스를 간단히 설명해보면, addEventListener를 사용하여 select 태그를 focus 했을 때 이벤트를 추가했다. option 여부가 기존에 생성된 적이 있는지를 확인하는 변수를 하나 두어, 한번 생성된 이후에는 다시 생성되지 않도록 했다. 

사실 처음에는 focus할 때만 option을 추가하고, blur가 되었을 경우에는 option을 제거하는 방식을 구현을 했다. 그랬더니 선택한 option도 제거되어 정상적으로 동작하지 않는 상황이 발생했다. 그래서 최초 클릭 시에만 목록을 생성하고, 그 이후에는 더 이상 생성하지 않고 유지하는 방식으로 구현을 했다.

createElement를 사용해서 요소를 생성하고, 필요한 속성과 값을 할당한 후에 appendChild를 통해 select 태그의 자식 요소로 추가했다.

![birth-select-f12](/assets/images/posts_img/web-toy-project-sign-up-and-in-page-2/birth-select-f12.gif)

개발자 도구로 확인해보면 select 태그 클릭 시 option들이 추가되는 것을 확인할 수 있다.

---

#### change 이벤트로 선택한 option 값 확인하기

위 select 태그에서 선택된 옵션을 확인해보자

![selected-option](/assets/images/posts_img/web-toy-project-sign-up-and-in-page-2/selected-option.png)

```html
<div id="print-date"></div>
```

선택된 조건을 출력하기 위한 div를 하나 추가했다.

```javascript
// birthYearEl focus 이벤트 리스너 함수 내부에 추가
YearOption.setAttribute('value', i)

// select된 option 확인
const selectedYearEl = document.querySelector('#print-date')
birthYearEl.addEventListener('change', (event) => {
  selectedYearEl.textContent = `Year of birth : ${event.target.value}`
});
```

먼저 위에서 구현한 focus 이벤트 리스너 함수 내부에 option 선택 시 value 속성을 추가하도록 수정했다. 이 value를 활용해서 선택된 값을 확인하려고 한다.

`addEventListener`의 `change` 이벤트를 활용하여 옵션 변경이 발생하면 `event.target.value`, 즉 option 태그에 추가했던 value 값을 출력하도록 했다.

![birth-select-print](/assets/images/posts_img/web-toy-project-sign-up-and-in-page-2/birth-select-print.gif)

(화면 녹화를 하면 select box가 보이지 않는다)  옵션을 클릭하면 위와 같이 선택한 옵션의 값이 잘 출력되는 것을 확인할 수 있다. 값을 눈으로 보기 위해 출력을 해준 것이고, 이제 이 선택된 값을 서버에 넘겨주면 된다.