[TOC]



# HTML & CSS



## HTML & CSS 기본 용어 & 개념

HTML은 문서 내용이 무엇인지 정의하고 구조화한다. 

- HTML의 목적은 보기좋게 꾸미는 게 아니라 문서 각 파트의 '의미'를 잘 전달하는 거다.

CSS는 문서를 폰트나 컬러 등을 활용해 꾸민다.

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

- Properties는 지정된 selector의 어떤 property(배경이냐, 테두리냐)을 설정할 건지 알려주는 것.

- Values는 property를 어떻게 설정해줄 건지(배경은 무슨 색이냐, 테두리 두께는 어느정도냐) 정하는 것.





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

- div 요소 vs span 요소

  div는 가로폭 모두 차지. span은 태그 안의 내용만 차지.

  div는 폭과 넓이 지정 가능. span 못함.

  div와 span은 HTML 태그이나 의미 전달이 목적 아님. 스타일링 목적임.

- p 요소

  단락으로 만들어줌. 두번째 단락부터는 한 줄 띄고 나온다. 

- b 요소 vs strong 요소

  둘 다 글자 진하게하는 효과 줌.  b요소는 문자열을 단순히 굵게 표시하고 strong 요소는 의미까지도 중요하다 전달.

- i 요소 vs em 요소

  둘 다 글자 기울임 효과 줌. i 요소는 단순히 기울이기만 하고 em 요소는 의미까지도 중요하다 전달. 





## CSS(Cascading Style Sheet) 사용하는 법

1. inline : HTML 특정 태그에 직접 style을 적용

   ```css
   <h1 style="color: red; fond-style: italic"> Hello world </h1>
   ```

2. HTML 내부에 STYLESHEET작성

   &lt;style&gt; 요소 이용,  보통 &lt;head&gt; 안에 넣음

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

   - css확장자로 별도의 stylesheet문서를 만들고 link 요소를 이용해 이 문서를 HTML 문서 안으로 불러온다. 

     - 별도의 문서 css문서(.css)는 HTML 파일이 위치한 폴더나 그 하위 폴더에  저장되어있어야 한다. 



       ```
       // css 파일이 html 파일과 동일한 폴더 안(=root directory)에 있는 경우
       <head>
         <link rel="stylesheet" href="main.css">
       </head>
       ```

       ```
       // css 파일이 html 파일과 다른 폴더 안(=stylesheets)에 있는 경우
       <head>
         <link rel="stylesheet" href="stylesheets/main.css">
       </head>
       ```

   - 스타일과 HTML은 분리가 되어야 좋다.


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



## JS 추가하기



### JS 추가 방법 3가지 : 인라인 스크립트, 외부 스크립트, 태그 내 직접 추가

1. 추가할 HTML 문서 내부에 직접 JS 코드 작성

   - &lt;/head&gt; 태그 전에 &lt;script&gt; element를 작성하고 그 안에 자바스크립트를 쓴다.
     - script 요소 안에 직접 작성한 자바스크립트 코드 = 인라인 자바스크립트 코드 

   ```html
   <script>
       // JavaScript goes here
   </script>
   
   // 예전에는 JS 외 스크립트 언어들이 자주 쓰여 브라우저에 JS임을 명시해줬어야하나 HTML5부터 type default가 JS가 되어 굳이 써줄 필요 없어졌다. 하위 버전에서도 작동하도록 하려면 써주는 게 안전하다. 
   <script type = "text/javascript"></script>
   ```

   - 자바스크립트 코드가 head에 위치해 다른 HTML 보다 먼저 실행되어 생기는 에러를 방지하기 위해 아래와 같이 HTML의 body가 모두 로딩된 뒤 실행될 수 있도록 한다.

   ```
   document.addEventListener("DOMContentLoaded", function() {
     ...
   });
   ```

2. 추가할 HTML 문서 외부에 JS 문서 작성 후 불러오기

   - 추가할 HTML 문서가 있는 폴더에 js 파일을 만들고 아래와 같이 script 태그의 attribute로 연결해준다.

   ```html
   <script src='script.js'></script>
   ```

3. HTML 태그 내에 직접 추가

   - HTML 태그그에 event attribute를 직접 추가해준다. 하지만 모든 태그에 일일이 손을 대야하고 코드가 길어질 경우 가독성도 좋지 않아 권장하지 않는다. 

   ```html
   <button onclick="createParagraph()">Click me!</button>
   ```



* script 태그에 src 속성을 사용해 외부 js 문서를 불러왔다면, &lt;script&gt; 태그 안에 js 내용이 있어도 무시. HTML 5에서는 에러로로 간주한다.
* 로컬이 아닌 다른 도메인에 있는 js 파일을 가져올 수도 있다. 직접 관리하는 도메인이나 신뢰할 수 있는 곳에서 관리하는 도메인 파일만 유의해서 가져와야 한다.

  ```html
  <script type="text/javascript" src="http://www.somewhere.com/afile.js"></script>
  ```


### JS 추가 위치

왜 추가 위치가 중요한가? 전통적으로, CSS파일이나 JS파일처럼 외부에서 참조하는 파일들을 한 곳에서 관리하기 위해  script 요소도 head 요소 안에 함께 넣어서 사용했다. 하지만 그럴 경우 JS 파일을 전부 내려받고, 파싱하고, 해석을 끝낼 때까지 body 안의 요소가 렌더링되지 않는다. 그래서 JS 파일을 불러올 동안 사용자는 텅 빈 화면만 보고 있어야 한다. 사용자가 페이지 로딩이 빠르다고 느낄 수 있도록 페이지 렌더링을 마친 뒤에 JS 코드를 처리하거나, JS코드와 페이지 렌더링을 동시에 처리하면 좋다.

-  body 요소 안에, 페이지 콘텐츠 마지막에 script 요소를 쓴다. (= &lt;/body&gt; 직전에 &lt;script&gt;를넣는다.)
- &lt;head&gt; 요소 안에서 script 요소의 defer나 async 속성을 활용하여  js파일을 불러온다.
  - defer는 문서의 콘텐츠를 완전히 파싱하고 표시할 때까지 스크립트 실행을 지연한다. script 요소가 head 요소 안에 있더라도 브라우저가 "</html>"을 만날 때 실행되는 것이다. DOMContentLoaded 이벤트보다 먼저 실행된다.
  - async는 문서의 콘텐츠 파싱과 동시에 스크립트를 실행한다. 마크업 순서대로 실행된다는 보장이 없기에 로드 순서가 중요하다면 defer 속성을 써야한다. load 이벤트 전에 반드시 실행되지만 DOMContentLoaded 이벤트보다는 앞설 수도 그 이후일 수도 있다. (load이벤트와 DOMContentLoaded에 대한 추가 이해 필요)
  - defer와 async는 HTML5부터 명세화되었기에 이를 지원하는 브라우저에서만 사용 가능하다.



### 브라우저가 JS를 지원하지 않는 경우

- noscript 요소를 활용해 대체 콘텐츠를 노출시킬 수 있다. 아래 문서가 자바스크립트를 지원하지 않는 브라우져에서 불러와진다면 페이지에는 This page...로 시작하는 문단만 나온다. 


  ```html
  <!DOCTYPE html>
  <haed>
      <title>Example HTML Page</title>
      <script type="text/javascript" defer="defer" src="example1.js"></script>
      <script type="text/javascript" defer="defer" src="example2.js"></script>
  </haed>
  <body>
      <noscript>
          <p> This page requires a JavaScript-enabled browser.</p>
      </noscript>
  </body>
  
  ```






# jQuery



### Method

.add()

어떤 요소를 추가로 선택할 때 사용한다. 

```html
//li 태그와 p 태그의 color를 red로 설정하고 싶을 때  
<script>
    $(document).ready(
        function(){
            $('li').add('p').css('color', 'red');
        }
    )
</script>
```

