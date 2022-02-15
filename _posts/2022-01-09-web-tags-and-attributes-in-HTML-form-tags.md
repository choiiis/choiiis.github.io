---
title:  "HTML form 내부의 태그와 속성들 : input, textarea, label, select"
excerpt: "form 내부의 태그와 속성들 한번에 정리하기"

categories:
  - Web
tags:
  - [Web, HTML]

permalink: /web/tags-and-attributes-in-HTML-form-tags/

toc: true
toc_sticky: true
 
date: 2022-01-09
last_modified_at: 2022-01-09
---

## 🦥 `<form>` 태그

<mark>입력 양식 전체를 감싸는 태그</mark>로, 텍스트/버튼/라디오 등의 컨트롤 요소 (control element)로 구성된다.

- **name** : form의 이름, 서버로 보내질 때 이름의 값으로 데이터 전송
- **action** : form이 전송되는 서버 url 또는 html 링크
- **method** : 전송 방법 설정. get은 default, post는 데이터를 url에 공개하지 않고 숨겨서 전송하는 방법
- **autocomplete** : 자동 완성. on으로 하면 form 전체에 자동 완성 허용

```html
<form name="profile" action="/action_page.php" 
      method="get" autocomplete="on">
  <input type="text" name="id">
  <select>
    <option value="blue">
  </select>
</form>
```
---

## 🦥 `<form>` 내부의 태그와 속성들

### 1. `<input>` 태그

#### 🌴 `<input>` 태그 속성

- **type** : 입력 형식
- **name** : 서버로 전송되는 데이터 이름

<br>

#### 🌴 `<input>` 태그 유형 (type 속성값)

▶ **`<input type="text">`**<br>
text 입력란

```html  
<!-- autofocus는 화면이 켜지고 커서의 첫 위치 -->
text: <input type="text" name="id" value="기본값" 
            placeholder=
             "칸 안에 default로 쓰여있는 값. 커서 올리면 사라짐"
            required pattern="[a-zA-Z].+[0-9]"
            autocomplete="off" autofocus>
```

**[실행 결과]**<br>
text: <input type="text" name="id" value="기본값" 
              placeholder="칸 안에 default로 쓰여있는 값. 커서 올리면 사라짐"
              required pattern="[a-zA-Z].+[0-9]"
              autocomplete="off" autofocus>

<br>

▶ **`<input type="password">`**<br>
비밀번호 입력란. 입력 내용이 보이지 않음.

```html
password: <input type="password" name="pwd" placeholder="PASSWORD">
```

**[실행 결과]**<br>
password: <input type="password" name="pwd" placeholder="PASSWORD">

<br>

▶ **`<input type="button">`**<br>

```html
<input type="button" value="전송" onclick="alert('hello world')">
```

**[실행 결과]**<br>
<input type="button" value="전송" onclick="alert('hello world')">

<br>

▶ **`<input type="submit">`**<br>
바로 form에 입력한 데이터를 보내주는 버튼

```html
<input type="submit" value="제출하기">
```

**[실행 결과]**<br>
<input type="submit" value="제출하기">

<br>

▶ **`<input type="reset">`**<br>
form에 입력한 모든 데이터 삭제

```html
  <input type="reset">
```

**[실행 결과]**<br>
<input type="reset" name="form 안의 모든 내용 삭제">

<br>

▶ **`<input type="radio">`**<br>
단일 선택

```html  
radio :<br>
<input type="radio" name="color" value="red"> 빨간색 <br>
<input type="radio" name="color" value="black" checked> 검은색
```

**[실행 결과]**<br>
radio :<br>
<input type="radio" name="color" value="red"> 빨간색 <br>
<input type="radio" name="color" value="black" checked> 검은색

<br>

▶ **`<input type="checkbox">`**<br>
다중 선택

```html  
checkbox :<br>
<input type="checkbox" name="color" value="red"> red<br>
<input type="checkbox" name="color" value="blue" checked> blue<br>
<input type="checkbox" name="color" value="black" checked> black<br>
```

**[실행 결과]**<br>
checkbox :<br>
<input type="checkbox" name="color" value="red"> red<br>
<input type="checkbox" name="color" value="blue" checked> blue<br>
<input type="checkbox" name="color" value="black" checked> black<br>

<br>

▶ **`<input type="file">`**<br>
file 업로드 컨트롤

- `method="post"` 일 때만 사용 가능
- `enctype` : form 데이터를 서버로 제출할 때 데이터가 인코딩 된 방법 명시
- `"multipart/form-data"` : 모든 문자를 인코딩하지 않음

```html
<form action="http://localhost/upload.php" method="post"
      enctype="multipart/form-data">
  <input type="file" name="selected-file">
  <input type="submit">
</form>
```

**[실행 결과]**<br>
<form action="http://localhost/upload.php" method="post"
      enctype="multipart/form-data">
  <input type="file" name="selected-file">
  <input type="submit">
</form>

<br>

▶ **`<input type="hidden">`**<br>
눈에 보이지 않는 정보를 서버쪽으로 보낼 때 사용. 서버로 choiiis라는 값 전송

```html
  <input type="hidden" name="hide" value="choiiis">
```

---

### 2. `<textarea>` 태그

▶ **`<textarea>`**<br>
여러 줄의 텍스트를 입력할 때

```html
<form>
  <p>textarea :
    <textarea cols="50" rows="3" 
              placeholder="default">입력하세요.</textarea>
  </p>
</form>
```

**[실행 결과]**<br>
<form>
  <p>textarea :
    <textarea cols="50" rows="3" 
              placeholder="default">입력하세요.</textarea>
  </p>
</form>

---

### 3. `<select>` 태그

▶ **`<select>`**<br>
드롭 다운 형식의 선택. 선택 항목은 option으로

```html
<form>
  <select name="color">
    <option value="서버에 전송될 값">red</option>
    <option value="blue">blue</option>
  </select>
  <!-- 다중 선택 multiple 추가 -->
  <select name="color2" multiple>
    <option value="black">검은색</option>
    <option value="blue">파란색</option>
  </select>
</form>
```

**[실행 결과]**<br> 
<form>
  <select name="color">
    <option value="서버에 전송될 값">red</option>
    <option value="blue">blue</option>
  </select>
  <!-- 다중 선택 multiple 추가 -->
  <select name="color2" multiple>
    <option value="black">검은색</option>
    <option value="blue">파란색</option>
  </select>
</form>

---

### 4. `<label>` 태그

▶  **`<label>`**

- control의 제목이 그것의 이름표라는 것을 명시하기 위해 사용
- checkbox나 radio에서 값을 클릭해도 표시될 수 있게 할 수 있음 (값이 radio의 label이라는 것을 표시해줘서)
- text에서는 화면상에서 label 클릭하면 text 입력 창으로 커서가 간다.

```html
<form action="">
<p>
  <label for="name_txt">text : </label>
  <input id="name_txt" type="text" name="id" value="default">
</p>
<p>
  <input id="color_rad1" type="radio" name="color" value="default">
  <label for="color_rad1">red</label>
  <input type="radio" name="color" value="default">blue
</p>
</form>
```

**[실행 결과]**<br>
<form action="">
<p>
  <label for="name_txt">text : </label>
  <input id="name_txt" type="text" name="id" value="default">
</p>
<p>
  <input id="color_rad1" type="radio" name="color" value="default">
  <label for="color_rad1">red</label>
  <input type="radio" name="color" value="default"> blue
</p>
</form>