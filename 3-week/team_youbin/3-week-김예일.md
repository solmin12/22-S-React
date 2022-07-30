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

### Script 언어와 컴파일 언어의 차이점
- JavaScript는 Script Language의 한 종류
특징으로는 프로그램이 실행되는 런타임에 코드가 해석됨
반면, Java, C언어와 같은 컴파일 언어는 컴파일 과정을 통해 소스코드가 해석되고 실행가능한 형태로 변환됨

### 리액트 REACT
- React 리액트란?
A javascript library for building user interfaces으로 사용자 인터페이스를 만들기 위한 자바스크립트 라이브러리를 의미

- React의 장점
빠른 업데이트 & 랜더링 속도  Virtual DOM을 사용함
Component-Based 형태로 레고 블록 조립하듯 컴포넌트를 모아서 개발함
재사용성(Reusability)을 가지어 개발 기간이 단축되고 유지보수가 용이함
ReactNative을 통해 모바일 개발도 지원함

- React의 단점
방대한 학습량
계속해서 뭔가 바뀌므로 꾸준히 공부
높은 상태관리 복잡도


### 프레임워크와 라이브러리
프레임워크는 프로그램의 흐름에 대한 제어 권환을 개발자가 아니라 직접 갖고 있는 반면,
라이브러리는 개발자가 필요한 부분만 가져다 사용하는 형태
즉, 라이브러리가 개발자가 가지는 제어 권한이 더 크다

### JSX
- JSX란?
A syntax extension to JavaScript으로 자바스크립트 문법을 확장시킨 것을 의미하며
JavaScript과 XML/HTML을 합친 것이다

- JSX의 장점
코드가 간결해져서 가독성을 높임
Injection Attacks 방어

### Rendering Elements
Elements
- React를 구성하는 가장 작은 블록들을 의미

Elements의 생김새
- React Elements는 자바스크립트 객체 형태로 존재함

React Elements의 특징
- 불변성(immutable)을 가지기에 Element 생성 후에 children이나 attribute를 변경할 수 없다.
- Element를 바꾸고 싶을 때는 변경 사항을 적용해 Element를 다시 생성하고 Element를 교체해 줘야 한다

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

Component 이름 규칙
- 항상 대문자로 시작하여 만들어야 한다.
- React는 소문자로 시작하는 Component를 DOM 태그로 인식하기 때문


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

### Component, Element, Props 예시
- Component는 붕어빵을 만드는 틀
- Element는 붕어빵이 완성된 것
- Props는 붕어빵의 속재료인 팥이나 슈크림 

### State
State란
- React component의 상태&데이터 즉, 변경 가능한 데이터
- 렌더링이나 데이터 흐름에 사용되는 값만 state에 포함시켜야 함
- 자바스크립트 객체 형태

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




