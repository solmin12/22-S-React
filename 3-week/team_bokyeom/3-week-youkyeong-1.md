# React

[https://www.inflearn.com/course/처음-만난-리액트#curriculum](https://www.inflearn.com/course/%EC%B2%98%EC%9D%8C-%EB%A7%8C%EB%82%9C-%EB%A6%AC%EC%95%A1%ED%8A%B8#curriculum)

## **HTML- Hyper Text Markup Language**

:웹사이트의 뼈대를 구성하기위해 사용되는 마크업 언어

- Markup→ 문서나 data를 처리하기 위해 문서에 추가되는 정보
- <head>:웹사이트의 속성을 담아 metadata로 불림

---



## **CSS-  cascading style sheets**

---



## **JavaScript**

### 정의

:프로그래밍 언어의 한 종류로 정식명칭은 ECMAScript이다.

:script언어이다.

- script언어→ 프로그램이 시작되는 runtime에 코드가 해석 및 실행됨(java, c와 같은 compile언어는 compile과정에서 source code를 해석해서 실행가능한 형태로 변환함)

### JS의 자료형

- data의 유형, 모든 변수는 자료형을 갖음
- 일반적인 프로그래밍 언어는 변수를 선언하는 시점에 해당 변수의 자료형이 결정되나, JS에서는 변수에 data가 대입되는 시점에 자료형 결정→ Dynamic Typing

### JS의 연산자

- 대입연산자 Assignment operator (=)
- 산술 연산자 Arithmetic operator(+ - / * % **)
- 증감 연산자 ++ — (postfix방식 a++, prefix방식 ++a)
- 관계 연산자 Relational operators=비교연산자 Comparison operators (< > ≤ ≥)
- 동등 연산자 Equality operators (== !=)
- 일치연산자 Strict equality operators (=== !==)자료형까지 동일한지 비교
- 이진 논리 연산자 Binary logical operators(&& ||)
- 조건부 연산자 Conditional operator=삼항연산자 Ternary operator(조건식 ? ture:false)

### JS 함수



```jsx
//function statement
function sum (a,b){
return a+b;
}

//arrow function expression
const multiply=(a,b)=>{
return a*b;
}
```

---



## **React**

:사용자 interface를 만들기위한 javascript library

### 장점

- 빠른 업데이트 및 렌더링 속도→ React 내부에서 Virtual DOM을 사용

<aside>
💡 - Virtual DOM은 실제 DOM과 웹페이지사이의 중간매개체역할

- 사용자와 상호작용하는 Webpage는 화면 update(dom 수정)가 수시로 이뤄지는데, 이 과정은 성능에 영향을 크게 미치고 비용이 많이 드는 작업임 → react는 update해야하는 상태의 변경(state change)발생시 최소한의 부분만 검색(compute diff)해 찾아서 update하고 re-render하여 사용자에게 보여줌

</aside>

- Component-based → 재사용성(Reusability) 향상

<aside>
💡 react내 모든 page는 Component(구성요소)로 구성되어져있으며, 하나의 component는 또 다른 여러개의 component의 조합으로 이뤄져있음.

재사용이 높은 개발→ 의존성을 낮추고 호환성을 높이는 개발

재사용성의 향상으로 개발기간의 단축, 유지보수 용이를 기대가능

</aside>

### 단점

- 방대한 학습량 →새로운 개념이 많으며, 변화되는 정보가 많아 지속적인 공부가 요구됨
- 높은 상태관리 복잡도

---



[SPA vs MPA와 SSR vs CSR 장단점 뜻정리 - 하나몬](https://hanamon.kr/spa-mpa-ssr-csr-%EC%9E%A5%EB%8B%A8%EC%A0%90-%EB%9C%BB%EC%A0%95%EB%A6%AC/)

## **SPA- single page Application**

:하나의 페이지(하나의 html file)만 존재하는 웹사이트/웹 어플리케이션

- 웹 어플리케이션에 필요한 정적리소스를 최초 한번에 다운로드 및 cache에 저장
- 초기에는 body tag의 내부가 비어있는 양상, 해당 page에 접속할때 해당하는(필요한) contents를 가져와서 동적으로 body tag의 내부를 갱신 → CSR(Client Side Rendering) 방식 렌더링
- SPA 방식이 모두 CSR인 것은 x

- 장단점
    
    장점
    
    - 필요한 부분만 갱신하므로 네이티브 앱에 가까운 자연스러운 페이지 이동 및 UX →UX 및 성능
    - 서버의 템플릿 연산을 클라이언트로 분산 →성능
    - 컴포넌트별 개발 → 생산성
    - 모바일 앱 개발시에도 동일한 API사용이 가능한 설계→ 생산성
    
    단점
    
    ```jsx
    <html>
    <head>
      <title>Single Page Application</title>
      <link rel="stylesheet" href="app.css" type="text/css">
    </head>
    <body>
      <div id="app"></div>
      <script src="app.js"></script>
    </body>
    </html>
    ```
    
    - 검색로봇에게 보이는 모든 페이지의 소스가 상단과 같아, 검색엔진이 색인 할 컨텐츠가 존재하지 않으므로 검색엔진최적화(SEO)가 어려움
    - 데이터 처리를 클라이언트에서 처리하기 때문에 해당 비즈니스 코드가 외부에 노출되는 보안적인 측면의 문제
    - JavaScript 파일을 번들링해서 한 번에 받기 때문에 초기 구동 속도가 느리다. (Webpack의 code splitting으로 해결 가능)
    - SSR에서는 사용자에 대한 정보를 서버측에서 세션으로 관리를 하지만 CSR 방식에서는 클라이언트측의 쿠키말고는 사용자에 대한 정보를 저장할 공간이 마땅치 않다

## **MPA -Multiple Page Application**

:여러 개(multiple)의 Page로 구성된 Application

- MPA는 새로운 페이지를 요청할 때마다 정적 리소스가 다운로드되어 매번 전체 페이지가 다시 렌더링 된다.
- SSR(Server Side Rendering) 방식 렌더링
- 장단점
    
    장점
    
    - 완성된 형태의 HTML file을 서버로부터 전달받아 검색엔진의 page 크롤링에 적합
    - 서버에서 렌더링해서 가져오므로 첫 로딩 매우 짧다(그러나 클라이언트가 JS 파일을 모두 다운로드하고 적용하기전 까지는 각각의 기능은 동작하지않는다.)
    
    단점
    
    - 페이지를 요청(새로고침 및 페이지이동)하는 경우 새로 리랜더링하기때문에 ‘깜빡’인다. (UX측면에서 불편함)
    - 페이지 요청이 들어오는 경우 불필요한 ****템플릿도 중복해서 로딩→ (성능)서버 렌더링으로 인한 부하 →(생산성)모바일 앱 개발시 추가적인 백엔드 작업이 요구되어 개발의 복잡성

---



## JSX

: A syntax extension to JavaScript (자바스크립트의 확장 문법)으로서 javaScript+XML/HTML

### 예제 코드 :

```jsx
const sample = <tag>text</tag>;
```

### 특징

- React에서 내부적으로 XML/HTML Code를 JS로 변환하는 과정을 거침

<aside>
💡 JSX문법을 사용하면 React에서 내부적으로 JSX code를 JS로 변환하는 역할을 해주는 React의 createElement(type, [props], […children])함수를 사용해 JS객체로 산출

</aside>

- React에서 createElement( )를 직접사용해도 되지만 JSX문법을 사용함으로서 생산성 및 코드의 가독성 향상
- JSX를 사용하다 js(변수 및 함수 등)를 사용하고 싶으면 XML, HTML 코드사이에 중괄호를 사용해서 이용 가능
- 태그의 속성(attribute)에 값을 넣고 싶은 경우에도 큰 따옴표 사이에 문자열을 넣거나, 중괄호 사이에 js코드를 넣는 방식을 사용

### 장점

- 간결한 코드
- 가독성 향상 →유지보수, 버그 발견 등
- Injection Attacks 방어 → 보안성 향상

<aside>
💡 Injection Attacks : 입력창에 문자나 숫자 같은 일반적인 값이 아닌 source code를 입력하여 실행하게 하는 해킹 방법

React DOM은 rendering이전에 imbedding된 값을 모두 문자열로 변환하므로 명시적으로 선언되지 않은 값은  { } 사이에 존재할 수 없다. → XSS(크로스 사이트 스크립팅 Cross Site Scripting)attack방어

</aside>
