# Team 유빈


# JavaScript

1 변수와 상수

 - 변수(variable) : 값이 여러 번 달라질 수 있는 데이터

 - 상수(constant) : 값을 한 번 지정하면 바뀌지 않는 데이터

 2 변수 선언의 규칙

변수 이름

영어 문자, 언더스코어(_), 숫자를 사용

첫 글자는 영어 문자, 언더스코어(_), 숫자를 사용

띄어쓰기나 기호는 허용하지 않는다.

 - 영어 대소문자를 구별하며 예약어는 변수 이름으로 사용할 수 없다.

 - 여러 단어를 연결할 때는 하이픈이나 언더스코어를 사용할 수 있고 중간에 대문자를 섞어 쓸 수도 있다.

 - 변수 이름은 의미 있게 작성한다.

 ### Script 언어와 컴파일 언어의 차이점
- JavaScript는 Script Language의 한 종류
특징으로는 프로그램이 실행되는 런타임에 코드가 해석됨
반면, Java, C언어와 같은 컴파일 언어는 컴파일 과정을 통해 소스코드가 해석되고 실행가능한 형태로 변환됨

 ### 자바스크립트로 무엇을 할까

- 웹 요소 제어
    1) 웹 요소를 가져와서 필요에 따라 스타일을 변경하거나 움직이게 할 수 있음
    2) 웹 사이트 UI 부분에 많이 활용
    3) 예) 마우스 포인터를 올렸을 때 펼쳐지는 메뉴, 한 화면에서 탭을 눌러 내용만 바뀌도록 하는 컨텐츠
    
- 다양한 라이브러리 사용 가능
    1) 웹을 중심으로 하는 서비스가 늘어나면서 브라우저에서 처리해야 할 일이 늘어남 -> 라이브러리와 프레임워크가 계속 등장
    2) 예) 시각화를 위한 d3.js, 머신러닝을 위한 tensorflow.js, DOM 조작을 위한 jQuery 등
    3) 예) 웹 애플리케이션 개발을 위한 React, Angular, Vue 등
    
- 웹 애플리케이션 제작
    1) 최근의 웹 사이트는 사용자와 실시간으로 정보를 주고 받으며 애플리케이션처럼 동작
    2) 예) 온라인 지도의 길찾기 서비스, 데이터 시각화 서비스, 공개된 API를 활용한 다양한 서비스

- 서버 구성 및 서버용 프로그램 제작 가능
    node.js : 프론트엔드 개발에 사용하던 자바스크립트를 백엔드 개발에서 사용할 수 있게 만든 프레임워크


# React

### SPA와 SSR
- Single Page Application SPA란?
 단일 페이지로 구성된 웹 애플리케이션

 - Server Side Rendering인 SSR이란?
 화면에 보여질 리소스를 서버로 요청하고, 서버로부터 받아온 리소스를 렌더링해서 화면 출력

 - SPA와 SSR의 차이점?
SPA는 렌더링의 역할을 서버에게 넘기지 않고 브라우저에서 처리하는 방식이어서
모든 정적 리소스를 최초에 한번 다운로드 하고, 이후 새로운 페이지 요청 시 페이지 갱신에 
필요한 데이터만을 전달받아 페이지를 갱신

- SPA의 장점?
전체적인 트래픽 감소와 렌더링에서 좋은 효율
빠른 화면 이동
앱처럼 자연스러운 사용자 경험(UX)를 제공
모듈화 또는 컴포넌트별 개발이 용이
백엔드&프론트엔드 구분 명확

- SPA의 단점?
초기 구동 속도가 느림
JavaScript를 통해 구현되므로 코드가 외부에 노출되는 보안적인 문제가 있다.
검색엔진 최적화(SEO)가 어렵다

### React

자바스크립트 UI라이브러리

### React 장단점

장점
- 빠른 업데이트와 렌더링 속도 - Virtual DOM 사용
- Component-Based(웹사이트를 컴포넌트들의 조합으로 만듬)
- 재사용성

단점
- 방대한 학습량
- 높은 상태관리 복잡도

### JSX

자바스크립트의 문법을 확장

JavaScript + XML/HTML

내부적으로 작성된 XML/HTML코드가 자바스크립트 코드로 변환된다. → React.createElement가 수행

JSX 장점

- 코드가 간결해진다.
- 가독성 향상
- Injection Attacks 방어 - 보안성 향상

### React Element

- 리액트 앱을 구성하는 가장 작은 블록들
- 화면에서 보이는 것들을 작성
- 자바스크립트 객체 형태로 존재

모든 React 컴포넌트는 `React.createElement`에 의해 React Element로 변환된다. 

```jsx
function Button(props){
	return(
			<button className={`bg-${props.color}`}>
					<b>
							{props.children}
					<b>
			</button>
		)
}

function ConfirmDoalog(props){
	return(
			<div>
				<p>내용을 확인하셨으면 확인 버튼을 눌러주세요.<p>
				<Button color=`green`>확인</Button>
			<div>
		)
}

// 랜더링 후
{
  type: 'div',
  props: {
    children : [
      {
        type: 'p',
        props: {
          children : '내용을 확인하셨으면 확인 버튼을 눌러주세요.'
        }
      },
      {
        type: 'button',
        props: {
          className: 'bg-green',
          children: {
            type: 'b',
            props:{
              childre: '확인'
            }
          }
        }
      }
    ]
  }
}
```

### React Element 특징

- immutable(불변성): 한번 Element를 생성 후에는 children이나 attributes를 바꿀 수 없다!
- 새로운 화면 갱신은 기존 Element에서 새로운 변경 사항을 적용해 생성한 Element로 변경
    
    → 불변성 때문

### Components
Component-Based (컴포넌트 기반)
- React는 레고 블록을 조립하듯 Components를 모아서 개발함

Component 만드는 방법
1. function component
- 장점은 간단한 코드
```jsx
 function Welcome(props) {
	return <h1> 안녕, {props.name} </h1>;
}
```
2. class component
- function component보다 몇 가지 추가적인 기능을 갖고 있다
```jsx
class Welcome extends React.Component {
	render() {
		return <h1>안녕, {this.props.name} </h1>;
	}
}
```

### Component 이름 규칙
- 항상 대문자로 시작하여 만들어야 한다.
- React는 소문자로 시작하는 Component를 DOM 태그로 인식하기 때문

### Function Component

props를 받아 React Element를 return하는 함수 형태의 컴포넌트

간결한 코드가 장점

### Class Component

React.Component를 상속받아 사용 → React.Component를 상속받았기 때문에 결과적으로 Class Component 또한 React Component이다.

Component의 이름은 항상 대문자로 시작해야 한다.

→ 소문자로 시작 시, React는 컴포넌트가 아니라 DOM태그로 인식

### Component 합성

Component를 여러 개 합쳐 Component를 만드는 것

### Component 추출

큰 컴포넌트에서 일부를 추출해 새로운 컴포넌트를 만드는 것

→ 재사용성과, 개발속도 상승

### Props
Props
- props는 속성을 의미하는 property를 줄여서 쓴 말
- 즉, React Component의 속성
- Component에 전달할 다양한 정보를 담고 있는 자바스크립트 객체

Props의 특징
- 읽기 전용(Read-Only)이기에 값을 변경할 수 없다

React component와 'Pure'
- 'Pure' 함수는 입력값을 변경하지 않으며, 같은 입력값에 항상 같은 출력값을 반환하는 것을 의미
- React component는 그들의 props에 관해서 pure 함수와 같은 역할을 해야한다
- 즉, props를 직접 바꿀 수 없고, 같은 props에 대해서는 항상 같은 결과를 보여줘야 함

Props 사용법
```jsx
function app(props) {
	Return (
		<profile 
			Name = “김예일”
			Introduction = “안녕하세요, 김예일입니다.”
			viewCount = {1500}
		/>
	);	
}
```

### State

React Component의 변경 가능한 데이터로 개발자가 정의해서 사용한다.

JavaScript 객체

정의된 state는 직접 수정하면 안된다.

State 사용법
- Component를 생성할 때 render() 함수보다 먼저 constructor() 함수를 적는다
- Component 생성자에서 super를 호출하기 전에는 this를 사용할 수 없기 때문
- 즉, 시작 부분에서 constructor() 함수가 component의 초기화를 시켜줘야 state에 값을 넣을 수 있다.

```jsx
 class App extends Component {
  constructor(props) {
    super(props);
      this.state={
				---
    }
  }
	render() {
    return (
      	<div className="App">
      	</div>
    );
  }
}
```
State 변경 방법
- state는 직접 수정하면 안 된다 (잘못된 방법)
```jsx
this. State = {
	Name: ‘yeil’
};
```
- setState() 함수를 통해 수정해야 한다 (정상적인 방법)
```jsx
this.setState( {
	Name: ‘yeil’
});
```
### Lifecycle 생명주기
-		출생 -->  인생  -->	사망
- Mounting 	Updating 	Unmounting
- Constructor
- ------ render --------
- componentDidmount  componentDidUpdate 	compoentWillUnmount
- component는 계속 존재하는 것이 아니라, 시간의 흐름에 따라 생성되고 업데이트 되다가 사라진다

