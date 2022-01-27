---
title:  "CSS 선택자 정리와 실습 예제"
excerpt: "선택자 select의 종류와 특징, 그리고 실습 코드와 실행 결과"

categories:
  - CSS
tags:
  - [Web, CSS]

permalink: /web/css-selectors-and-examples/

toc: true
toc_sticky: true
 
date: 2022-01-11
last_modified_at: 2022-01-11
---

## 🦥 CSS?

### Cascading Style Sheets

body 내부의 style attribute를 `<head>`에 `<style>`로 따로 빼서 html을 꾸며준다.

---

## 🦥 선택자 select

디자인 할 태그를 선택하고, 그 대상에 적용할 속성을 입력<br>
<mark>선택자 { 속성 : 값 ; 속성2 : 값2 }</mark> 형태로 구성

### 🌴 선택자 종류

- **태그 선택자** : `<>` 안의 태그명으로 선택 ex. `<ul>`, `<li>`, `<div>` 등
- **class 선택자** : HTML 태그의 속성에 `class="클래스명"`을 쓰고, CSS에서는 `.class명` 형태로 사용
- **id 선택자** : HTML 태그의 속성에 `id="id명"`을 쓰고, CSS에서는 `#id명` 형태로 사용

### 🌴 선택자 특징

- 여러 요소가 같은 class 값 가질 수 있지만 같은 id 값은 가질 수 없음
- class="클래스1 클래스2"와 같이 여러 개의 클래스명을 입력하면 두 클래스(클래스1, 클래스2)에 모두 포함될 수 있음

### 🌴 선택자 사용 예시

- `.fruit>#yellow` : fruit(class) 바로 하위의 yellow(id) 만 선택
- `ul, ol` : ul과 ol을 모두 선택.
- `ul li` : ul 아래의 모든 li (바로 하위 아니어도 됨)

---

## 실습 코드

```html
<html>
<head>
    <style>
        /* 태그 선택자 */
        ol {
            color: blue;
        }
        
        /* class 선택자 */
        .color {
            color: green;
        }
        
        /* id 선택자 */
        #yellow_col {
            color: yellow;
        }
        .col>.yellow {}
    
        .col>#yellow_col {}
    
        ul, li {}
        
        .fruit .yellow {}
        
    </style>
</head>
<body>
    <div class="lists">
        <ul class="color col" id="color_id">
            <li>Red</li>
            <li>Blue</li>
            <li class="yellow" id="yellow_col">Yellow</li>
        </ul>
        <ol class="fruit">
            <li>Apple</li>
            <li style="color: pink">Orange</li>
            <li class="yellow">Lemon</li>
        </ol>
    </div>
</body>
</html>
```

**[실행 결과]**

<html>
<head>
    <style>
        /* 태그 선택자 */
        ol {
            color: blue;
        }
        /* class 선택자 */
        .color {
            color: green;
        }
        /* id 선택자 */
        #yellow_col {
            color: yellow;
        }
        .col>.yellow {}
        .col>#yellow_col {}
        ul, li {}
        .fruit .yellow {}
    </style>
</head>
<body>
    <div class="lists">
        <ul class="color col" id="color_id">
            <li>Red</li>
            <li>Blue</li>
            <li class="yellow" id="yellow_col">Yellow</li>
        </ul>
        <ol class="fruit">
            <li>Apple</li>
            <li style="color: pink">Orange</li>
            <li class="yellow">Lemon</li>
        </ol>
    </div>
</body>
</html>