---
title: CSS 정리 by 드림코딩
tags: [CSS]
date: 2021-09-12 15:18:00 +09:00
categories: [CSS] 
---

## CSS 정의 특성

CSS : Cascading Style Sheets

`Cascading` : 작은폭포처럼 연속해서 떨어지는 모습
따라서 style 적용하는 순서가 있다.

`Author style` → .css 파일

`User style` → darkmode, 글자 크기 조절 브라우저에서 제공한는 스타일

`Browser` → Browser에서 기본적으로 지정된 스타일

순서 `Auther style` → `User style` → `Broswer`

Auther style 이 없으면 User style에서,

User style이 없으면 Browser에서 style을 찾는다.

## 선택자

Universal  `*`

Type         `Tag`

ID              `#id`

Class         `.class`

State         `:`

Attribute  `[]`

## CSS 정렬 특성

1. `display: inline` 은 텍스트처럼 ( 가로 )

    <a>, <i>, <span>, <abbr>, <img>, <strong>, <b>, <input>, <sub>, <br>, <code>, <em>, <small>, <tt>, <map>, <textarea>, <label>, <sup>, <q>, <button>, <cite>

2. `display: block` 은쌓이는 상자처럼 (세로) 

    <address>, <article>, <aside>, <blockgquote>, <canvas>, <dd>, <div>, <dl>, <hr>, <header>, <form>,<h1>, <h2>, <h3>, <h4>, <h5>, <h6>, <table>, <pre>, <ul>, <p>, <ol>, <video>

## **사이트**

CSS Reference [https://developer.mozilla.org/ko/docs/Web/CSS/Reference](https://developer.mozilla.org/ko/docs/Web/CSS/Reference)

css 선택자 연습 사이트 :  [https://flukeout.github.io/](https://flukeout.github.io/)

## HTML 코드

```html
<!DOCTYPE html>
<html>
<head>
  <meta charset="utf-8">
  <meta name="viewport" content="width=device-width">
  <title>JS Bin</title>
</head>
<body>
  <ol>
    <li id="special">First</li>
    <li> Second</li>
  </ol>
  <h1 id="special">Hello</h1>
  <button>Button 1</button>
  <button>Button 1</button>
  <div class="red"> sdf </div>
  <div class="blue"></div>
  <a href="naver.com">Naver</a>
  <a href="googlenaver.com">Google</a>
  <a>Empty</a>
</body>
</html>
```

### 1. * 모든 요소 선택

```css
* {
  color: blue;
}
```

### 2. tag  해당 tag이름 모두 선택

```css
li {
  color: green;
}
```

### 3. #id   해당 id 선택

```css
#special {
  color: pink;
}
```

### 4. 해당 태그의 id 선택

```css

li#special {
  color: brown;
}
```

### 5.  .  해당 class 모두 선택

```css
.red {
  width: 100px;
  height: 100px;
  padding; 20px;
  background: yellow;
}
```

### 6. css 속성 요약

```css
.red {
  border-style: 2px;
  border-style: solid;
  border-color: pink;
}

.red {
  border: 2px dashed red;
}
```

### 7. hover  : 해당 요소에 mouse over 즉 마우스가 올라갈 시 event 발생

```css
button:hover {
  color: red;
  background: black;
}
```

### 8. [ ] 특성선택자 : 주어진 특성의 존재 여부나 그 값에 따라 요소 선택

```css
a[href] {
  color: green;
}
```

### 9. 특성선택자 검색 옵션

```css
a[href^="naver"] {   ^="value" value로 시작하는 특성 찾기  
  color: black;
}

a[href$=".com"] {    $="value" value로 끝나는 특성 찾기 
  color: white;
}

a[href*="naver"] {   ^="value" value를 포함하는 특성 찾기 
  color: black;
}
```

### 10. Position

```css

.box {
  background: blue;
  left: 20px;
  top: 20px;
  position: relative;
  
```

- `relative`  : 이전 요소에 자연스럽게 연결하여 위치 지정
- `fixed`       : .continer에서 벗어나 페이지 상에서 움직인다.
- `absolute` : item이 담겨있는 상자, 즉 .container를 기준으로 움직인다.
- `relative` : 원래 자리에서 상대적으로 움직인다
- `sticky`    : scrolling 되어도 그자리 그대로 붙어있는다.

### 11. %, vh

```css
  height: 100%;
	height: 100vh;
```

`%`  : 가까운 부모 요소에 상대적인 영향을 받는드ㅏ.

`vh` : viewport height의 약자로써, 화면 크기를 기준으로 한 높이이다.  

출처

- 드림코딩 엘리 [https://www.youtube.com/watch?v=gGebK7lWnCk&t=358s](https://www.youtube.com/watch?v=gGebK7lWnCk&t=358s)