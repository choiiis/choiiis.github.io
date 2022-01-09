---
title:  "HTML 태그와 속성 정리 : 소스 코드와 실행 결과"
excerpt: "HTML이란? 그리고 여러가지 HTML 태그와 속성 한번에 정리하기"

categories:
  - Web
tags:
  - [Web, HTML]

permalink: /web/about-html-tags-and-attributes/

toc: true
toc_sticky: true
 
date: 2022-01-09
last_modified_at: 2022-01-09
---

웹 개발의 기초 중의 기초라고 할 수 있는 HTML  
head와 body안의 여러가지 태그와 속성들에 대해 하나하나 알아보자.  


## 🦥 HTML이란?

>HTML은 HyperText Markup Language의 약자

### 1. HyperText

하이퍼텍스트를 찾아봤더니 많은 양의 정보를 효과적으로 연결하고 관리하기 위한 기계에서 비롯되었다고 한다. 글을 읽거나 사전을 찾을 때처럼 처음부터 순차적으로 책장을 넘기는 것이 아닌, <mark>사용자가 선택하여 원하는 방향으로 정보를 찾아나가는</mark> 방식이라고 할 수 있다. 따라서, HTML에서는 정보 간의 연결이 중요하다.

### 2. Markup Langugage

Markup Language는 마크로 둘러싸인 언어라는 뜻이다. 문서의 골격, 즉 구조에 대한 정보를 작성한 언어라고 할 수 있다.

---

## 🦥 HTML 태그와 속성

### 🌴 `<head>` 안의 태그와 속성들

▶ **`<title>`**<br>
  페이지의 제목을 나타내는 태그, 브라우저 탭에 나타난다.

▶ **`<meta>`**<br>
  문서에 대한 정보 제공하는 태그
  - **charset** : 문자 인코딩 정보

    ```html
    <meta charset="utf-8">
    ```

  - **author** : 문서 작성자 정보

    ```html
    <meta name="author" content="choiiis">
    ```

  - **keyword** : 문서의 키워드

    ```html
    <meta name="keyword" content="devlog, HTML">
    ```

  - **description** : 문서에 대한 설명

    ```html
    <meta name="description" content="HTML tags">
    ```

  - **viewport** : 디바이스에 따라 화면 fit

    ```html
    <meta name="viewport" 
        content="width=device-width, initial-scale=1.0">
    ```

---

### 🌴 `<body>` 안의 태그와 속성들

▶ **`<h1>`, `<h2>`, ..., `<h6>`**<br>
  heading, 제목/소제목 등을 나타낸다. 볼드체의 큰 폰트 크기

▶ **`<strong>`**<br>
  글자를 두껍게 강조한다.

▶ **`<p>`**<br>
  약간의 간격을 주어 문단을 나눠주는 역할을 한다.

▶ **`<br>`**<br>
  줄바꿈 문자

▶ **`<a>`**<br>
  anchor, 링크를 통해 다른 문서에 연결한다.
  - `href` : 연결할 링크
  - `target="_block"` : 새 탭에서 열기
  - `title` : 마우스를 대면 나오는 타이틀
  
  ```html
  <a href="https://choiiis.github.io/" 
    target="_block" title="choiiis의 devlog">
  ```

<br>

▶ **`<ol>`, `<ul>`, `<li>`**<br>
  리스트 관련 태그
  - `<ol>` : 순서가 있는 리스트 생성 (리스트 번호는 자동 생성)
  - `<ul>` : 순서가 없는 리스트 생성
  - `<li>` : 리스트에 속하는 요소들에 대한 태그

  ```html
  <ol>
    <li>apple</li>
    <li>orange</li>
    <li>lemon</li>
  </ol>
  <ul>
    <li>red</li>
    <li>orange</li>
    <li>yellow</li>
  </ul>
  ```

<br>

▶ **`<img>`**<br>
  이미지 삽입 태그

  ```html
  <img src="img.jpg" height="300" width="400" 
   alt="이미지 누락시 속성값 화면 표시" title="마우스 대면 뜨는 문구"></img>
  ```

<br>

▶ **`<table>`**<br>
  표 관련 태그

  ```html
  <table>
    <thead>
      <tr>
        <th>표의 맨 윗 부분 요소</th>
      </tr>
    </thead>
    <tr>
      <td>표의 데이터, 요소 하나하나 td로 묶어줘야 함(thead는 th)</td>
      <!--묶는 행/열 중 가장 처음 것에 쓰고 나머지 데이터 삭제-->
      <td rowspan="2"> 두 행을 묶음 (수직 방향).</td>
    </tr>
    <tfoot>
      <tr>
        <td>표의 맨 아래 부분 요소</td>
        <td colspan="3"> 세 열을 묶음 (수평 방향).</td>
      </tr>
    </tfoot>
  </table>
  ```

<br>

▶ **`<form>`**<br>
  입력 양식 전체를 감싸는 태그. form은 컨트롤 요소(control element)로 구성된다. 텍스트, 버튼, 라디오 등이 컨트롤
  - name : form의 이름, 서버로 보내질 때 이름의 값으로 데이터 전송
  - action : form이 전송되는 서버 url 또는 html 링크
  - method : 전송 방법 설정. get은 default, post는 데이터를 url에 공개하지 않고 숨겨서 전송하는 방법
  - autocomplete : 자동 완성. on으로 하면 form 전체에 자동 완성 허용

  ```html
  <form name="profile" action="/action_page.php" method="get" 
        autocomplete="on">
    <input type="text" name="id">
    <select>
      <option value="blue">
    </select>
  </form>
  ```

  ✅ form 태그 추가 정리는 여기로 >> [[HTML] <form> 태그 정리](https://choiiis.github.io/web/basics-of-html-form-tags/)

<br>

▶ **`<iframe>`**<br>
  웹페이지에 다른 웹페이지를 추가하는 태그
  - 다른 웹페이지를 내부에 추가하거나, 유튜브 동영상 화면 추가할 때도 사용
  - 위험할 수 있음 => sandox 사용해서 삽입된 웹페이지의 스크립트 실행되지 않도록 한다.
  - 유튜브 동영상 추가하려면 '공유 - 퍼가기'에서 복사

  ```html
  <iframe src="https://choiiis.github.io" 
    width="100%" height="auto"></iframe>

  <!-- 유튜브 주소 추가할 때-->
  <iframe width="560" height="315" 
          src="https://www.youtube.com/embed/NAi690rUpMk" 
          frameborder="0" allow="accelerometer; autoplay; 
              encrypted-media; gyroscope; picture-in-picture" 
          allowfullscreen></iframe>

  <!-- sandox로 삽입된 외부 소스의 스크립트가 실행되지 않도록 함 -->
  <iframe src="iframe_src.html" frameborder="0" sandbox></iframe>
  ```
  
  **[실행 결과]**

  <iframe src="https://choiiis.github.io/" width="100%" height="auto"></iframe>
  <br>
  <iframe width="560" height="315" src="https://www.youtube.com/embed/NAi690rUpMk" frameborder="0" allow="accelerometer; autoplay; encrypted-media; >gyroscope; picture-in-picture" allowfullscreen></iframe>

<br>

▶ **`<video>`**
  동영상을 추가하는 태그
  - controls : 동영상을 컨트롤하는 툴 보이게
  - ~~autoplay : 자동으로 재생 (바뀌었는지 안됨)~~

  ```html
  <video width="600" controls>
    <source src="baby.mp4">
    <source src="baby.ogv">
  </video>
  ```

<br>

▶ **Can I Use 웹페이지**

이 웹페이지를 통해 어떤 태그나 속성을 현재 쓸 수 있는지 여부에 대해서 알 수 있다<br>
[https://caniuse.com/](https://caniuse.com/)

---

## 🦥 HTML semantic element(tag)

### 🌴 semantic vs. non-semantic

- **semantic tag** : 내용을 명확하게 정의한 태그들 ex. `<header>`, `<nav>`, `<article>`
- **non-semantic tag** : 내용에 대해서 알 수 없는 태그들 ex. `<div>`, `<span>`

<br>

### 🌴 semantic tag (의미론적 태그)

문서의 정보를 보다 잘 표현하기 위해 사용하는 의미를 갖는 태그들
- `<header>` : 문서나 section의 헤더에 오는 태그. 문서 내에 여러 개가 존재할 수 있음.
- `<footer>` : 문서의 정보를 담고 있는 태그. ex. 문서의 저자, copyright 정보, term of use 링크
- `<main>` : 해당 페이지의 메인 내용. 문서 내에서 한번만 사용
- `<section>` : 관련 있는 주제들끼리 grouping 해주는 태그 (문서 구획). 보통 header를 갖음.
- `<article>` : 독립적으로 의미가 있는 컨텐츠. 웹사이트의 나머지 부분과 독립적으로 읽더라도 의미를 이해할 수 있는 내용을 주로 담음. ex. 블로그 포스트나 기사
- `<nav>` : navigation links. 문서의 major link들 담는 태그. ex. 메뉴, 목차, 색인
- `<aside>` : 문서의 content의 옆쪽에 위치하여 내용과 관계가 적음. 광고를 추가하기도 함.
- `<figure>` : 이미지와 캡션을 묶어주는 태그

```html
<html>
  <head>
    <title></title>
    <meta>
  </head>
  <body>
    <header>
      	<h1></h1>
    </header>
    <section>
      <nav>
        <ol>
          <li></li>
          <li></li>
       	</ol>
      </nav>
      <main>
        <article>
          <h2></h2>
		</article>
		<article>
          <h2></h2>
		</article>
      </main>
      <aside></aside>
    </section>
    <footer>
      <ul>
        <li></li>
        <li></li>
      </ul>
    </footer>
  </body>
</html>
```