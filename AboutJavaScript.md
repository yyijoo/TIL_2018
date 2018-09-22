# About JavaScript



### 자바스크립트 역사

- 1995년 넷스케이프의 브랜든 아이흐(Breaden Eich)가 개발.
- 처음엔 Mocha, 나중엔 LiveScript라고 불림. 홍보 목적으로 당시 트렌드였던 자바의 이름을 차용.
- 처음 등장했을 때 주요 목적은 이전엔 펄 같은 서버언어가 담당하던 '입력 유효성 검사' 였다. 필수 필드가 비어있거나 입력된 값이 잘못된 형식인지 판단할 때 서버를 거치지 않고, 자바스크립트로 클라이언트에서 판단을 마칠 수 있게 되었다.
- 1996년 마이크로소프트가 인터넷 익스플로러를 통해 자바스크립트를 독자적으로 구현해 여러 버전이 생기게되었고, 이후 표준화되었다. 이 표준은 유럽 컴퓨터 제작자 협회(European Computer Manufacturer Association : ECMA, 에크마)에 의해 제안된다.  



### 자바스크립트 구현

자바스크립트는 다음 세 부분으로 구성된다.

1. 코어(ECMAScript)

2. 문서 객체 모델 (DOM)

   - 웹 페이지 콘텐츠를 조작할 수 있는 메서드와 인터페이스를 제공한다. 

   - XML을 HTML에서 사용할 수 있도록 확장한 API(Application Programming Interface)다.
     - XML은 W3C(World Wide Web Consortium. 월드와이드웹을 위한 표준을 개발하고 장려하는 조직)에서 개발된 다목적 마크업 언어다. 인터넷에 연결된 시스템끼리 데이터를 쉽게 주고 받을 수 있게 하여 HTML의 한계를 극복할 목적으로 만들어졌다.
   - HTML 전체 페이지를 노드의 계층 구조로 변환한다. DOM API를 통해 노드를 쉽게 제거, 추가, 교체 수정할 수 있다. 
   - 익스플로러와 내비게이터가 서로 다른 동적 HTML(DHTML)을 지원하면서 DOM도 표준이 생겼다. 브라우저 별로 지원하는 DOM 레벨 수준 다르다. 
     - DOM 레벨 1 포함 모듈
       - DOM코어 : XML 기반 문서를 노드 트리로 변환)
       - DOM HTML : HTML에 밀접한 객체와 메서드를 DOM코어에 추가해 확장한 것)
     - DOM 레벨 2에 추가된 모듈
       - DOM Views : 문서의 다양한 뷰를 추적하는 인터페이스 (ex. CSS 스타일 적용 전후) 
       - DOM 이벤트 : 이벤트와 이벤트 처리에 관한 인터페이스
       - DOM 스타일 : CSS를 통해 요소의 스타일을 바꾸는 인터페이스
       - DOM 이동과 범위 : 문서 트리를 이동하고 조작하는 인터페이스
     - DOM 레벨 3에 추가된 모듈
       - DOM 로드와 저장 : DOM을 더 확장해 문서를 저장하고 불러오는 통일된 방법
       - DOM 유효성 검사 : 문서가 유효한지 검사하는 방법
   - 자바스크립트에 묶은 모델은 아니다! 

3. 브라우저 객체 모델 (BOM)

   - 브라우저와 상호작용하는 메서드와 인터페이스를 제공한다.

     

### 기타

아래 내용 지속 업데이트 & 정리 필요

- JavaScript의 컴파일러는 두 번 동작한다.
  ㄴ complie을 두 번 돈다. 먼저 선언만 위로 hoisting 해준다. 그리고나서 다시 읽음.
- 자바스크립트는 변수에 값을 선언할 때 메모리를 자동으로 할당한다.
- 자바스크립트는 고급인터프리터.
- 가비지콜렉터는 할당된 메모리가 필요없어지면 할당을 해제함. 

Objective-Oriented Programming

- 전통적인 프로그래밍 관점(함수들의 집합, 단순한 컴퓨터의 명렁어 목록)에 반한 관계성있는 객체들의 집합이라는 관점. 
- Java, Python, Ruby 등 객체지향언어에는 Class라는 개념을 활용하나, 자바스크립트는 Class라는 개념 대신 기존의 객체를 복사하여 새로운 객체를 생성하는 Prototype 언어다. 


