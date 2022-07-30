# Team 민수

# 리액트란
[SPA vs MPA와 SSR vs CSR 장단점 뜻정리 - 하나몬](https://hanamon.kr/spa-mpa-ssr-csr-%EC%9E%A5%EB%8B%A8%EC%A0%90-%EB%9C%BB%EC%A0%95%EB%A6%AC/)

## MPA(multiple page application)

- 여러개의 페이지로 구성된 application
- 새로운 페이지를 요청할 때마다 정적 리소스(HTML, CSS, JavaScript) 다운됨. 매번 전체 페이지가 다시 렌더링.
- SSR(Sever Side Rendering) 방식의 렌더링

### 장점

- SEO 관점에서 유리하다.
  - MPA는 완성된 형태의 HTML 파일을 서버로부터 받음
  - 따라서 검색엔진이 페이지를 크롤링하기에 적합함.
- 첫 로딩이 매우 짧음
  - 서버에서 미리 렌더링 후 가져옴
  - 그러나 클라이언트가 JS 파일을 모두 다운하고 적용하기 전까지는 기능 동작X

### 단점

- 새로운 페이지로 이동하면 ‘깜빡'인다.(UX)
  - 매 페이지 요청마다 새로고침. 전체를 다 다시 렌더링.
- 페이지 이동시 불필요한 템플릿도 중복해서 로딩(성능저하)
- 서버 렌더링에 따른 부하
- 모바일 앱 개발시 추가적인 백엔드 작업.

## SPA(single page application)

- 하나의 페이지로 구성된 application
- 필요한 모든 정적 리소스 최초 한번에 다운로드. 이후 새로운 페이지 요청시 페이지 갱신에 필요한 데이터만 전달받아서 페이지 갱신. 기존 페이지의 내부를 수정해서 보여준다.
- 리로딩 없이 필요한 부분만 서버로부터 받아서 화면을 갱신함.
- 필요한 부분만 가져오기 때문에 네이티브 앱에 가까운 자연스러운 페이지 이동과 UX를 제공할 수 있음
- Angular, React, Vue 등의 지원.
- SPA는 CSR(Client Side Rendering) 방식의 렌더링
- 검색엔진 최적화 어려움.
  - 검색엔진이 색인을 할만한 컨텐츠가 없음.

### 장점

1. 자연스러운 UX
   - 전체 페이지를 업데이트할 필요 X → 빠르고 깜빡이지 않음
2. 필요한 리소스만 부분적으로 로딩 → 성능 향상
   - SPA의 application은 서버에 정적 리소스 한번만 요청. 받은 데이터를 전부 저장. 캐시(Cache)
3. 서버의 템플릿 연산을 클라이언트로 분산으로 성능 향상
4. 컴포넌드별 개발 용이 (생산성)
5. 모바일 앱 개발 시 동일한 API 사용 설계가능

### 단점

1. JavaScript 파일을 번들링해서 한번에 받기 때문에 초기 구동속도 느림 ( Webpack 의 code splitting)
2. 검색엔친 죄적화 어려움 (SSR로 해결)
3. 보안 이슈
   - SSR에서는 사용자에 대한 정보를 서버측에서 관리. CSR은 클라이언트 측의 쿠키 이외에는 X

- SPA 방식이 모두 CSR 인 것은 아님.

## SSR

MPA 는 페이지를 이동할 때마다 새로운 페이지 요청.

모든 템플릿은 서버 연산을 통해 렌더링 후 완성된 페이지 형태로 응답

서버 사이드 렌더링의 장점은 SEO이다. 전통적인 MPA의 경우 브라우저에서 JavaScript 코드가 동작하기 전에도 완성된 형태의 템플릿 (HTML에 데이터가 삽입된 상태)을 서버로 부터 전달받는다. 이 때문에 검색로봇이 페이지를 크롤링하기에 매우 적합하다

## CSR

최초에 한번 서버에서 전체 페이지 로딩해서 보여준 후 사용자의 요청이 올 때마다 리소스를 서버에서 제공한 후 클라이언트가 해석하고 렌더링.

## JSX

[JSX 소개 - React](https://ko.reactjs.org/docs/introducing-jsx.html)

JSX는 자바스크립트의 문법을 확장한 것.

# Components (Lifecycle)

리액트는 컴포넌트 기반으로, 레고 블럭을 조립하듯 컴포넌트들을 모아서 개발

## React component의 입출력

React component 입력 : Props

React component 출력 : React element

React component는 속성을 받아 React element로 변환 시켜주는 것
<br><br>

## Component

- Class Component

ES6문법 중 Class를 이용하여 만든 Component

React.Component를 상속받아서 만듦

```jsx
class Welcome extends React.Component{
		render(){
				return <h1>안녕, {this.props.name}</h1>;
	}
}
```

- Function Component

```jsx
function Welcome(props){
		return <h1>안녕, {props.name}</h1>;
}
```

## Component 이름

Component 이름은 항상 대문자로 시작해야 한다.

소문자로 쓰면 DOM태그로 인식함
<br><br>

## Component 합성 

컴포넌트는 자신의 출력에 다른 컴포넌트 참조 가능.

위에서 만든 Welcome을 여러번 렌더링하는 App 컴포넌트 만들 수 있음.
<br><br>


## Component 추출

재사용 가능한 컴포넌트를 만들어두는 것. 중첩구조로 이루어지면 불편할 수 있는 경우, 각 구성요소를 개별적으로 재사용할 수 있게 만든다.

## Life Cylce


- 출생 (Mounting)
1. constructor 실행 ( 컴포넌트의 state 정의)
2. Component 렌더링
3. componentDidMount 호출

- 인생(Updating)
1. New props, setState(), forceUpdate()로 업데이트 됨
2. componentDidUpdate 호출

- 사망(Ummounting)

  - 상위 컴퍼넌트에서 현재 컴퍼넌트를 더이상 화면에 표시하지 않을 때 사망함.

  - 사망하기 직전에 componentWillUnmount 함수 호출

컴포넌트가 계속 존재하는 것이 아니라, 시간의 흐름에 따라 생성되고 업데이트 되다가 사라짐

# Props & State


### Props란

Property의 줄인말, Component의 속성을 말함.

위의 그림을 보면 붕어빵에 들어가는 속 재료를 Props로 나타낼 수 있다.

컴포넌트에 전달할 다양한 정보를 담고 있는 자바스크립트 객체

### Props의 특징

1. Read-Only

  읽을 수만 있다 = 값을 변경 할 수 없다

  즉, 새로운 컴포넌트에 새로운 Props를 전달하여 새로운 element를 만들어서 변경해야 함

2. React에서는 모든 React 컴포넌트는 자신의 props 를 다룰 때 반드시 순수함수처럼 동작해야함

```jsx
function sum(a, b) {
  return a + b;
}
```
순수함수: 위처럼 입력값을 바꾸지 않고 항상 동일한 입력값에 동일한 결과를 반환.

```jsx
function withdraw(account, amount) {
  account.total -= amount;
}
```

위 함수는 입력값을 바꾸기 때문에 순수함수가 아님.

React에서는 모든 React 컴포넌트는 자신의 props 를 다룰 때 반드시 순수함수처럼 동작해야함.

### Props 사용법

```jsx
function App(props){
	return(
			<Profile
						name="상연"
						intrioduction="안녕하세요, 상연입니다."
						viewCount={1500}
				/>
		);
}
```

## State란

리액트 Component의 변경 가능한 데이터

state는 개발자가 정의함

렌더링이나 데이터 흐름에 사용되는 값만 state에 포함시켜야함

자바스크립트 객체

```jsx
class LikeButton extends React.Component {
	constructor(props){           // 생성자
		super(props);

		this.state = {             //State 정의
				liked : false
		};
	}
	...
}
```

state는 직접 수정하면 안된다

```jsx
// state를 직접 수정 (잘못된 예시)
this.state = {
	name.'Inje'
};

// setState 함수를 통한 수정 (옳바른 예시)
this.setState({
		name:'Inje'
});
```
