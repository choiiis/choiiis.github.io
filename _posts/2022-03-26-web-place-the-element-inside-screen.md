---
title:  "Javascript로 원형 div를 화면에서 벗어나지 않게 출력하기"
excerpt: "요소를 화면 밖으로 나가지 않게 하고 화면 크기에 맞춰 조절하기"

categories:
  - Web
tags:
  - [Web, CSS, JS]

permalink: /web/place-the-element-inside-screen/

toc: true
toc_sticky: true
 
date: 2022-03-26
last_modified_at: 2022-03-26
---

### 원형 div element의 지름을 화면 크기에 따라 조절하기

![inside-browser.gif](/assets/images/posts_img/web-place-the-element-inside-screen/inside-browser.gif)

```js
window.addEventListener('resize', function() {
  focusEl.style.width = focusEl.style.height = getBallDiameter() + "px"
})

function getBallDiameter() {
  return Math.floor((bodyEl.clientWidth + bodyEl.clientHeight) * 0.1)
}
```

html과 body의 width와 height를 100%로 했기 때문에, body의 크기는 화면 크기와 동일하게 따라서 바뀐다. 그래서 화면에 resize 이벤트가 발생할 때마다 body의 가로 세로 합의 10% 정도로 요소의 지름을 설정했다.

<br>

<p class="codepen" data-height="300" data-default-tab="html,result" data-slug-hash="XWVpedV" data-user="choiiis" style="height: 300px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/choiiis/pen/XWVpedV">
  ball</a> by choiiis (<a href="https://codepen.io/choiiis">@choiiis</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://cpwebassets.codepen.io/assets/embed/ei.js"></script>

---

### 요소를 화면 내부에 스크롤바 없이 유지하기

![top-left](/assets/images/posts_img/web-place-the-element-inside-screen/top-left.png)

Canvas를 이용하지 않아서 원형 요소를 div로 생성을 했기 떄문에, 도형의 위치는 left, top으로 조절했다. top과 left의 값은 위에서 노란색으로 표현한 경계선의 위치를 나타낸다. 만약 div 요소의 left를 100%, top을 100%로 설정을 한다면, 요소가 기존 화면 범위를 넘어가면서 스크롤 바가 생긴다. 노란색 경계 부분이 100%의 위치에 오기 때문이다.

<br>

<p class="codepen" data-height="300" data-default-tab="html,result" data-slug-hash="xxpgroE" data-user="choiiis" style="height: 300px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/choiiis/pen/xxpgroE">
  ball : not inside the browser</a> by choiiis (<a href="https://codepen.io/choiiis">@choiiis</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://cpwebassets.codepen.io/assets/embed/ei.js"></script>

<br>

```js
function getPos(d) {
  return {
    'w': bodyEl.clientWidth - d,
    'h': bodyEl.clientHeight - d
  }
}

focusEl.style.left = getPos(focusEl.clientWidth)['w'] + "px"
focusEl.style.top = getPos(focusEl.clientWidth)['h'] + "px"
```

100%로 주던 top, left 값을 (화면 크기 - 지름)의 값으로 변경했다. 이제 기존 화면 범위를 벗어나지 않고 화면의 우측 하단에 잘 나타난다. 

<br>

<p class="codepen" data-height="300" data-default-tab="html,result" data-slug-hash="ZEvLJJW" data-user="choiiis" style="height: 300px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/choiiis/pen/ZEvLJJW">
  ball : inside the browser</a> by choiiis (<a href="https://codepen.io/choiiis">@choiiis</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://cpwebassets.codepen.io/assets/embed/ei.js"></script>

<br>

그리고 혹시 화면 크기를 조절하면서 요소가 화면 밖으로 나가서 스크롤바가 생긴다면, 아래와 같이 resize를 할 때마다 요소의 위치까지 다시 설정해주면 된다.

```js
// screen resized
window.addEventListener('resize', function() {
  resetFocus()
})

function resetFocus() {
  // set diameter
  focusEl.style.width = focusEl.style.height = getFocusDiameter() + "px"
  // place on the center
  focusEl.style.left = (bodyEl.clientWidth - focusEl.clientWidth) * 0.5 + "px"
  focusEl.style.top = (bodyEl.clientHeight - focusEl.clientWidth) * 0.5 + "px"
}
```