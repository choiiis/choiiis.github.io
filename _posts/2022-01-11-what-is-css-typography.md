---
title:  "CSS 타이포그래피 속성 정리 & 실습 코드"
excerpt: "글씨체나 정렬, 색상 등에 관련된 타이포그래피에 대해 실습을 통해서 알아보기"

categories:
  - Web
tags:
  - [Web, CSS]

permalink: /web/what-is-css-typography/

toc: true
toc_sticky: true
 
date: 2022-01-11
last_modified_at: 2022-01-11
---

## 🦥 타이포그래피란?

> 활판으로 하는 인쇄술, 편집 디자인 등에서 활자의 서체나 글자 배치 따위를 구성하고 표현하는 일을 타이포그래피라고 한다.

---

## 🦥 타이포그래피 속성

### 🌴 font-size : 폰트 사이즈 관련

**[활용 예시]**

- `font-size : 20px`
- `font-size : 1rem`
- `font-size : 1.2em`

\* em/rem 사용 권장. px는 고정값이라서 화면 크기에 따라 가변적이지 못해서 별로

<br>

### 🌴 color : 폰트 색상 관련

**[활용 예시]**

- `color : blue`
- `color : #00FF00`
- `color : rgb(255,0,255)`

<br>

### 🌴 font-family : 글씨체 관련

- 폰트를 여러 개 선택하고 그 중 가능한 것으로 나타나게 할 수도 있음<br>
   ex) Courier, Georgia, "Gill Sans" 이렇게 쓰면 앞에서부터 있는 것으로 출력
- 폰트 이름 중간에 띄어쓰기가 있으면 `" "` 처리
- 같은 폰트 내에서도 아래와 같이 다양한 형태로 보여줄 수 있음

**[활용 예시]**

- `font-family : Courier, serif;` : 장식
- `font-family : Courier, sans-serif;` : 장식이 없는 것
- `font-family : Courier, cursive;` : 흘림체
- `font-family : Courier, fantasy;` : 두껍고 진한? 글씨체
- `font-family : Courier, monospace;` : 고정 폭

<br>

### 🌴 font-weight : 폰트 가중치나 굵기 관련

**[활용 예시]**

- `font-weight : normal`
- `font-weight : bold`
- `font-weight : bolder` : 부모 weight보다 bold
- `font-weight : lighter` : 부모 weight보다 light

<br>

### 🌴 text-align : 텍스트 정렬 관련

**[활용 예시]**

- `text-align : justify` : 양쪽 정렬
- `text-align : left` : 왼쪽 정렬
- `text-align : right` : 오른쪽 정렬
- `text-align : center` : 가운데 정렬

<br>

### 🌴 line-height : 줄 간격 관련

**[활용 예시]**

`line-height : 2`

<br>

### 🌴 font : font 속성 여러 개 한 번에 처리

font-style > font-variant > font-weight > font-size/line-height > font-family 순서로 입력

**[활용 예시]**

`font : bold 2rem Courier, monospace;`

---

## 실습 코드

```html
<html>
<head>
   <link href="https://fonts.googleapis.com/css2?family=
               Chelsea+Market&display=swap" rel="stylesheet">
    <style>
        #word {
            font-size: 2rem;
            color: yellowgreen;
            font-family: Courier, Georgia, "Gill Sans", monospace;
            font-weight: bold;
            line-height: 2;
            text-align: center;
        }
        #word2 {
            font-size: 2rem;
            font-family: 'Chelsea Market', cursive;
            text-align: right;
        }
    </style>
</head>
<body>
   <p>
    <div id="word">
      Lorem ipsum dolor sit amet, consectetur adipiscing elit.
      Suspendisse sollicitudin ac odio vel molestie.
    </div>
   </p>
   <p>
    <div id="word2">
       Nam placerat rhoncus quam a venenatis. 
      Phasellus faucibus scelerisque nisi non auctor.
    </div>
    </p>
</body>
</html>
```

**[실행 결과]**

<html>
<head>
   <link href="https://fonts.googleapis.com/css2?family=
               Chelsea+Market&display=swap" rel="stylesheet">
    <style>
        #word {
            font-size: 2rem;
            color: yellowgreen;
            font-family: Courier, Georgia, "Gill Sans", monospace;
            font-weight: bold;
            line-height: 2;
            text-align: center;
        }
        #word2 {
            font-size: 2rem;
            font-family: 'Chelsea Market', cursive;
            text-align: right;
        }
    </style>
</head>
<body>
   <p>
    <div id="word">
      Lorem ipsum dolor sit amet, consectetur adipiscing elit.
      Suspendisse sollicitudin ac odio vel molestie.
    </div>
   </p>
   <p>
    <div id="word2">
       Nam placerat rhoncus quam a venenatis. 
      Phasellus faucibus scelerisque nisi non auctor.
    </div>
    </p>
</body>
</html>