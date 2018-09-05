[TOC]



# HTML & CSS



## HTML & CSS 기본 용어 & 개념

HTML은 문서 내용이 무엇인지 정의하고 구조화한다. 

- HTML의 목적은 보기좋게 꾸미는 게 아니라 문서 각 파트의 '의미'를 잘 전달하는 거다.

CSS는 해당 문서를 폰트나 컬러 등을 활용해 꾸민다.

- elements는 페이지 안의 구조와 콘텐츠의 목적을 알려주는 지표다. 시작 태그와 종료 태그로 이루어진 모든 명령어. 

- tags는 elements의 일부로 시작 태그와 종료 태그 두 종류가 있음.

- attributes는 element에 대한 추가 정보를 제공하는 속성. attribute는 시작 태그 안에 element의 이름 뒤에 들어온다.

- Selector는 정확히 어떤 element를 꾸며줄 건지 알려주는 것. 

  - Type Selector는 같은 element 타입에 모두 동일 style 적용 

  - Class Selector는 element와 상관없이 그룹을 나눠 그룹별 style 적용. Class를 만들어 원하는 element에 class를 부여. 다른 element라도 동일 class가 적용될 수 있음. 한 element에 2개 이상의 class 설정할 수 있음.

    ```
    <h1 class="red italic"> Hello world </h1>
    .red { color : red }
    .italic { font-style: italic }
    ```

  - Id Selector는 각각의 element에 고유한 ID를 부여함으로써, ID별 style을 적용할 수 있게해줌. 단 하나의 element가 유일한 ID 하나만 적용할 수 있음.

    ```
    <h1 id="hello"> Hello world </h1>
    <h1 id="code">code states</h1>
    ```

    

- Properties는 지정된 selector의 어떤 성분을 설정할 건지 알려주는 것.

- Values는 property를 어떻게 설정해줄 건지!





self-closing elements

- `<br>`
- `<embed>`
- `<hr>`
- `<img>`
- `<input>`
- `<link>`
- `<meta>`
- `<param>`
- `<source>`
- `<wbr>`



## HTML 태그

### HTML 구조 관련 태그

```html
<html>
    <head>
        <meta name = 'description' content='태그는 태그 내부에 값을 넣을 수 있을 뿐 아니라 태그마다 속성 부여 가능'>
        
    </head>
        <body> // body는 보이는 부분
            <style>
                // CSS 스타일 추가
            </style>
            <script>
                // javascript 추가
            </script>
        </body>
</html>
```

<meta> 태그는 보이지 않는 정보를 제공하는데 쓰이는 태그. ex) 페이지의 설명 요약, 핵심 키워드, 제작자, 크롤링 정책 등



### HTML 콘텐츠 관련 태그

- <div> vs. <span>

  div는 가로폭 모두 차지. span은 태그 안의 내용만 차지

  div는 폭과 넓이 지정 가능. span 못함

  

<a href = 'url'>

<ul>, <li>

<img>

<iframe>

<br>

<table>, <thead>, <tbody>, <tr>, <th>, <td>

<code>, <pre>

### HTML 폼 관련 태그

<form>

<input> (type: text, checkbox, color, date, password...)

<button>

<textarea>

<select>, <option>

<b>, <font>, <center> 등은 권장하지 않는다 왜냐면..





## CSS(Cascading Style Sheet) 사용하는 법

1. inline : HTML 특정 태그에 직접 style을 적용

   ```
   <h1 style="color: red; fond-style: italic"> Hello world </h1>
   ```

   

2. HTML 내부에 STYLESHEET작성

   <style> 태그 이용

   보통 <head> 태그 안에 넣음

   ```html
   <!DOCTYPE html>
   <html>
       <head>
           <style>
               h1 {
                   color: red;
                   font-style: italic;
               }
           </style>
       </head>
   ```

   



3. HTML 외부에 STYLESHEET 작성

   - css확장자로 별도의 stylesheet문서를 만들고 <link> 태그를 이용해 이 문서를 HTML 문서 안으로 불러오기. 

     - 별도의 문서 css문서(.css)는 HTML 파일이 위치한 폴더나 그 하위 폴더에  저장되어있어야 함. 

       1) css 파일이 html 파일과 동일한 폴더 안(=root directory)에 있는 경우

       ```
       <head>
         <link rel="stylesheet" href="main.css">
       </head>
       ```

       ```
       <head>
         <link rel="stylesheet" href="stylesheets/main.css">
       </head>
       ```

       

   - 스타일과 HTML은 분리가 되어야 좋음. 

## CSS Resets 사용하기

브라우져별로 element별 기본 스타일이 다르다. 이를 통일시켜주기 위해 css resets를 사용한다.

CSS는 기존에 설정된 걸 지우고 재설정하게 해준다.

가장 일반적으로 쓰는 리셋은 Eric Meyer's reset https://meyerweb.com/eric/tools/css/reset/



## HTML Event Attributes

[w3schools events attributes reference](https://www.w3schools.com/tags/ref_eventattributes.asp)



```html
<button onclick='myFunction()'>Click me</button>
```



# With JavaScript



## 자바스크립트 추가하기

추가 방법

1. 추가할 HTML 문서 내부에 직접 추가

   - </head> 태그 전에 <script> element를 작성하고 그 안에 자바스크립트를 쓴다.

   ```html
   <script>
       // JavaScript goes here
   </script>
   ```

   - 자바스크립트 코드가 head에 위치해 다른 HTML 보다 먼저 실행되어 생기는 에러를 방지하기 위해 아래와 같이 HTML의 body가 모두 로딩된 뒤 실행될 수 있도록 한다.

   ```
   document.addEventListener("DOMContentLoaded", function() {
     ...
   });
   ```

   

2. 추가할 HTML 문서 외부에 자바스크립트 문서 작성 후 불러오기

   - 추가할 HTML 문서가 있는 폴더에 js 파일을 만들고 아래와 같이 script 태그의 attribute로 연결해준다.

   ```html
   <script src='script.js'></script>
   ```

3. HTML 태그 내에 직접 추가

   - HTML 태그그에 event attribute를 직접 추가해준다. 하지만 모든 태그에 일일이 손을 대야하고 코드가 길어질 경우 가독성도 좋지 않아 권장하지 않는다. 

   ```html
   <button onclick="createParagraph()">Click me!</button>
   ```



# jQuery



