---
title:  "마우스를 따라 움직이는 조명 효과 구현하기"
excerpt: "CSS, JS를 활용하여 스포트라이트 효과 만들기"

categories:
  - Web
tags:
  - [Web, CSS, JS]

permalink: /web/how-to-make-spotlight-focus/

toc: true
toc_sticky: true
 
date: 2022-03-27
last_modified_at: 2022-03-27
---

## 포커스 애니메이션 구현하기

![focus-sample.jpg](/assets/images/posts_img/web-how-to-make-spotlight-focus/focus-sample.jpg)

가끔 애니메이션이 시작할 때 이런 조명이 이곳 저곳 움직이다가 전체를 밝히는 씬이 등장한다. 비슷한 느낌으로 웹에서 동작하도록 해보았는데, Canvas를 사용하지 않고 CSS와 JS만으로 구현했다.

---

## 개발 기록

### 조명 효과 spotlight CSS 구현하기

![inside-browser.gif](/assets/images/posts_img/web-how-to-make-spotlight-focus/light-css.png)

```js
  background: radial-gradient(
    circle 50px at 100px 100px,
    rgba(0, 0, 0, 0.01) 0%,
    rgba(0, 0, 0, 0.5) 70%,
    rgba(0, 0, 0, 0.96) 100%);
```

실제 핀 조명 이미지를 찾아보면서 비슷한 형태로 요소를 만들어봤다. `background`에 `radial-gradient`로 특정 위치에 원형 그라데이션을 추가하여 구현했다. 중앙은 투명하게, 경계로 갈수록 불투명하게 그라데이션을 주어 구멍이 뚫린 듯한 효과가 난다.

<br>

<p class="codepen" data-height="300" data-default-tab="html,result" data-slug-hash="XWVMzjy" data-editable="true" data-user="choiiis" style="height: 300px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/choiiis/pen/XWVMzjy">
  spotlight</a> by choiiis (<a href="https://codepen.io/choiiis">@choiiis</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://cpwebassets.codepen.io/assets/embed/ei.js"></script>

<br>

---

### 마우스를 따라 움직이는 극장 핀 조명

![theater-light-move](/assets/images/posts_img/web-how-to-make-spotlight-focus/theater-light-move.gif)

조명의 느낌을 조금 더 살리기 위해 흰 배경에서 극장 커튼 이미지로 변경했다. 

```js
document.addEventListener("mousemove", trackMouse = (event) => {
  const focusElX = event.clientX + "px"
  const focusElY = event.clientY + "px"
  focusEl.style.background = `radial-gradient(
    circle ${getScreenAvg() * 0.1}px at ${focusElX} ${focusElY},
    rgba(0, 0, 0, 0.01) 0%,
    rgba(0, 0, 0, 0.5) 70%,
    rgba(0, 0, 0, 0.96) 100%`
})
```

그리고 조명이 마우스를 따라 이동하도록 하기 위해, document에 이벤트 리스너를 추가하여 `mousemove` 이벤트가 발생할 경우 `trackMouse` 함수가 실행되도록 했다. 이 함수에서 원형 그라데이션의 반지름을 화면의 가로 세로의 평균값 * 0.1로 설정해주고, 위치는 focusElX(=event.clientX = 마우스 X 좌표), focusElY(=event.clientY = 마우스 Y 좌표)로 설정했다.

<br>

<p class="codepen" data-height="300" data-default-tab="html,result" data-slug-hash="XWVMEjy" data-user="choiiis" style="height: 300px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/choiiis/pen/XWVMEjy">
  theater spotlight</a> by choiiis (<a href="https://codepen.io/choiiis">@choiiis</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://cpwebassets.codepen.io/assets/embed/ei.js"></script>

<br>

---

### 마우스 클릭 시 조명이 퍼지면서 밝아지도록 구현

![spotlight-zoom-in-and-out](/assets/images/posts_img/web-how-to-make-spotlight-focus/spotlight-zoom-in-and-out.gif)

마우스 클릭 시 조명의 반지름 크기가 살짝 줄어들었다가 커지면서 화면 전체를 밝히도록 하려고 한다. 조명은 `background`에 원형 형태의 그라데이션을 구현한 것이다 보니, `transition`으로 자연스럽게 변경되도록 처리할 수가 없었다. 그래서 반지름을 조금씩 반복해서 줄이고 늘리는 방법으로 구현해보았다.

```js
// 클릭 이벤트 내부의 함수
// zoomIn 반복 실행 3ms에 0.001씩 100번 (총 300ms)
zoomIn = setInterval(() => {
      i += 1
      focusEl.style.background = `radial-gradient(
        circle ${getScreenAvg() * (0.2-(0.001*i))}px at ${eventX} ${eventY},
        rgba(0, 0, 0, 0.01) 0%,
        rgba(0, 0, 0, 0.5) 70%,
        rgba(0, 0, 0, 0.96) 100%`
    }, 3)
  
    // 300ms 후 zoomIn Interval 종료
    setTimeout(() => {
      // zoomIn 반복 끝
      clearInterval(zoomIn)
    }, 300)
  }
})
```

조명의 크기가 줄어드는 `zoomIn` 함수에서는 `setInterval` 함수로 반복적으로 i의 값을 증가시켜 원의 반지름을 점점 줄여나갔다. 그리고 100회 반복 후(300ms 후) `clearInterval`을 호출하여 Interval이 종료되도록 했다.  

```js
    // zoomIn 반복 끝
    setTimeout(() => {
      clearInterval(zoomIn)
     
     // zoomOut 반복 실행 10ms에 0.02씩 100번(1000ms)
      zoomOut = setInterval(() => {
        j += 1
        focusEl.style.background = `radial-gradient(
          circle ${getScreenAvg() * (0.1+(0.02*j))}px at ${eventX} ${eventY},
          rgba(0, 0, 0, 0.01) 0%,
          rgba(0, 0, 0, 0.5) 70%,
          rgba(0, 0, 0, 0.96) 100%`
      }, 10)
    
      // zoomOut 반복 끝
      setTimeout(() => {
        clearInterval(zoomOut)
        isEventRunning = false
      }, 1000)
    }, 300)
  }
```

한 가지 더 신경 썼던 부분은 조명이 줄어든 '이후'에 늘어나야 한다는 점이다. 그래서 `zoomIn`의 Interval이 종료되는 `setTimeout` 함수 내부에 `zoomOut` 함수를 만들어 순차적으로 수행되도록 했다.

<br>

<p class="codepen" data-height="300" data-default-tab="html,result" data-slug-hash="rNpyqYG" data-editable="true" data-user="choiiis" style="height: 300px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/choiiis/pen/rNpyqYG">
  Theater Spotlight Follows the Mouse Pointer</a> by choiiis (<a href="https://codepen.io/choiiis">@choiiis</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://cpwebassets.codepen.io/assets/embed/ei.js"></script>

<br>

---

## 문제 해결

### 이벤트 처리 중에 동일 이벤트 발생 막기

```js
let isEventRunning = false
document.addEventListener("click", clickFocus = (event) => {
  if(!isEventRunning) {
    isEventRunning = true // 이벤트 시작
    ...
  // zoomOut 반복 끝
  setTimeout(() => {
    clearInterval(zoomOut)
    isEventRunning = false // 이벤트 종료
  }, 1000)
  ...
})
```

조명이 줄어들었다가 다시 커지는 클릭 이벤트 처리 중에 또 다시 클릭을 할 경우, 이벤트가 중복으로 처리되면서 비정상적으로 동작하는 문제가 발생했다. 이 현상을 막기 위해 `isEventRunning` 변수를 하나 생성해서 이 변수가 `false`일 때만 이벤트가 발생되도록 했다. 이 변수는 이벤트 처리 시작 시에 true로, 끝날 때에 false로 값을 설정하여 이벤트 처리 중에만 true 값이 되도록 했다.

---

### 이벤트 처리 후 더 이상 실행되지 않도록 하기(리스너 제거하기)

![error-2](/assets/images/posts_img/web-how-to-make-spotlight-focus/error-2.gif)

```js
document.addEventListener("click", clickFocus = (event) => {
  if(!isEventRunning) {
    isEventRunning = true
    window.removeEventListener('resize', resizeScreen)
    document.removeEventListener("mousemove", trackMouse)
    document.removeEventListener("click", clickFocus)
    ...
```

두 번째 문제는 이벤트 실행 이후에 마우스 움직임 이벤트, resize 이벤트 등이 실행될 경우 초기 상태로 돌아간다는 것이다. 클릭 이벤트가 실행된 이후에는 다른 이벤트들이 동작하지 않도록 처리를 해주었다. `removeEventListener`를 활용해서 click 이벤트의 리스너 안에서 `resize`, `mousemove`, 그리고 실행 중인 `click` 이벤트까지 제거해주었다.

주목할 부분은 `addEventListener` 내부에서 동일 Event의 `removeEventListener`를 실행하는 것도 가능하다는 점이다. 이렇게 하면 이벤트가 한 번만 발생하도록, 즉 한번 발생한 이후에 더 이상 발생하지 않도록 할 수 있다.

---

## 전체 소스 코드

GitHub에서 확인하기 : [https://github.com/choiiis/html-css-toy-projects/tree/main/spotlight-focus](https://github.com/choiiis/html-css-toy-projects/tree/main/spotlight-focus)

CodePen에서 확인하기 : [https://codepen.io/choiiis/pen/rNpyqYG](https://codepen.io/choiiis/pen/rNpyqYG)

---
