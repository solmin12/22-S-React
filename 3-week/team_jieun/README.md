# Team 지은
## 리액트 탄생 배경

- **JavaScript를 사용하여 HTML로 구성한 UI를 제어할 때** DOM을 변형시키는 작업을 거쳐야한다. → 사용자와 상호작용이 없는 웹페이지라면 상관이 없지만, interaction이 자주 발생하면 **관리하기도 힘들고** **코드가 난잡해 질 수 있어서  최대한 깔끔하게 정리하여 유지 보수를 하는 것도 힘들 수 있다.**

- 이에 AngularJs, Ember등의 프레임워크가 만들어졌는데, **이 프레임워크들은** 자바스크립트의 특정 값이 바뀌면 DOM의 속성이 바뀌도록 연결해주어서 업데이트 하는 작업을 간소화해주는 방식이다.

- **리액트의 경우** 조금 다른 발상에서 만들어졌다. 리액트는 어떠한 상태가 바뀌었을 때 그 상태에 따라 DOM을 어떻게 업데이트 할 지 규칙을 정하는 것이 아니라 처음부터 모든걸 새로 만들어서 보여준다면 어떨까? 라는 아이디어에서 개발이 시작되었다.
    - 그래서 만들어진게 **Virtual DOM**이라는 것이다. Virtual DOM은 가상의 DOM인데 메모리에 가상으로 존재하기에 실제로 존재하는 DOM을 보여주는 것보다 속도가 훨씬 빠르다.(실제 DOM은 브라우저가 화면을 표현하는데 필요한 정보가 모두 들어있어서 실제 DOM은 무거움) 그래서 리액트는 상태가 업데이트 되면 업데이트가 필요한 곳의 UI를 Virtual DOM을 통해서 렌더링한다. (최소한의 변경사항만 반영)
    - 그 후 실제 브라우저에 보여지고 있는 DOM과 비교를 한 후, 차이가 있는 곳을 감지해서 실제 DOM에 패치시켜준다.

## Node.js

- js로 네트워크 애플리케이션을 개발할 수 있게 해주는 환경
- 브라우저에서만 돌아가던 js를 외부 응용 프로그램으로 빼서 브라우저 없이 돌아갈 수 있게 자체 엔진이라고 생각하면 된다.
→ 그렇기 때문에 node.js로 js를 활용해 웹을 벗어나 서버도 만들 수 있고 다양한 것들이 제작 가능하게 된다.

## npm(node package manager)

- node.js를 위한 package manager 
- package manager(: 프로젝트를 하면서 필요한 다양한 외부 패키지들의 버전, 의존성을 관리해주는 것)
- node.js를 설치하면 자동으로 설치된다.

## 리액트란 ?

- UI를 만들기 위한 js 프레임워크 → 자주 사용되는 기능을 정리해 모아둔 것
- 장점
    - 빠른 업데이트와 렌더링 속도
    - component 기반 → 재사용이 용이하다.
    - 활발한 지식 공유 & 커뮤니티 (github의 facebook/react 활용하기!)
    - react를 학습한 후, react native를 활용하여 모바일 웹도 개발이 가능해진다.
    
- 단점
    - 방대한 학습량
        
        Virtual Dom, JSX, Component, State, Props등등의 새로운 개념들이 많음
        
        버전 업데이트를 통해 계속해서 정보들이 추가되거나 바뀜 →새로 공부해야 함
        
    - 높은 상태 관리 복잡도
        
        state는 리액트 컴포넌트의 상태를 의미하는데 프로젝트의 규모가 커지면 상태 관리 규모도 커지게 되어 관리가 힘들다.
        

## Import 문

- 리액트 코드에서 가장 상단에 위치한 import 문은 App.js가 다른 곳에 정의된 코드들을 사용할 수 있게 해준다.

```jsx
//react 라이브러리를 불러오는 명령문
//건너뛰면 오류 발생
import React from 'react';
```

- 특정 파일을 import하고 싶을 때는 경로 지정을 해서 가져오면 끝

## Export 문

- 변수, 함수, 클래스 앞에 export 키워드를 붙여 모듈의 기능을 외부에서 사용할 수 있도록 내보낸다.

# JSX

- jsx는 자바스크립트의 확장 문법이다.
- jsx = 자바스크립트 + XML / HTML
- XML/HTML 코드를 자바스크립트 코드로 변환하는 역할을 한다. 하나의 파일에 자바 스크립트와 HTML을 동시에 작성할 수 있어 편리하다.
- 리액트에서 JSX를 사용하는 것이 필수는 아니지만, 코드가 간결해지고, 가독성이 높으며 버그를 발견하기가 쉽다는 장점을 가지고 있어서 사용한다.

# Elements

: react app을 구성하는 가장 작은 블록들

- 화면에서 보이는 것들을 기술한다.
- react elements는 js 객체 형태로 존재한다.
- 컴포넌트 렌더링을 위해 모든 컴포넌트가 createElement 함수를 통해서 elements로 변환된다.

<aside>
💡 ‘불변성’을 가지고 있음 → 한번 생성된 elements는 변하지 않는다 → elements 생성 후에는 children이나 attributes를 바꿀 수 없다.

- ex) component : 붕어빵 틀, element : 완성된 붕어빵

</aside>

### elements 렌더링하기

```jsx
<div id="root"></div> -> root DOM Node
//모든 리액트 앱에 필수적으로 들어가는 중요한 코드
//div 안에 있는 모든 것이 리액트 DOM에 의해 관리된다.
```

- 리액트 elements가 렌더링되는 과정은 virtual DOM에서 실제 DOM으로 이동하는 과정
- elements를 업데이트하려면?

 - 새롭게 업데이트 된 elements를 기존의 elements하고 바꿔치기한다!

## 웹 프레임워크의 작동 원리

- 기존의 웹 프레임워크는 MVC 방식을 활용했다.
    - **MVC**란 ? 정보를 담당하는 모델(**M**odel), 화면을 담당하는 뷰(**V**eiw), 구동을 담당하는 컨트롤러(**C**ontroller)을 뜻한다.
- MVC방식은 코드 관리를 효율적으로 할 수 있다는 장점이 있으나 각 요소의 의존성이 높아 재활용이 어렵다는 단점이 존재한다. (하나의 요소만을 바꾸기가 쉽지 않다.)
- 하지만, 우리가 보는 웹 사이트들의 화면은 각 요소가 비슷하고 반복적으로 사용이 된다는 것을 알 수 있다.
- 그렇다면 의존성도 낮고 코드를 효율적으로 관리 할 수 있는 것이 없을까 ? 해서 등장한 것이 component라고 한다.
    - MVC의 뷰를 독립적으로 구성하며 재사용도 할 수 있게 되었다.
    - component를 통해 새로운 컴포넌트를 쉽게 만들 수 있게 되었다.

## Component

- 작은 component들이 모여서 하나의 component를 구성하고 이러한 component들이 모여서 하나의 페이지가 생성된다.
- props를 통해 입력을 받고 React element를 통해 출력한다.
- Function Component
    - 일종의 함수라고 생각하면 편하다.
    - 사용하기 간단하다는 장점이 존재한다. 아래 코드는 함수 component의 예시이다. (순수함수 형태로 작성된 것을 볼 수 있다.)
        
        ```jsx
        function Welcome(props){
        	return <h1>안녕, {props.name}</h1>;
        }
        ```
        
- Class Component (불편하다는 의견이 많아 잘 사용하지 않는다.)
    - 리액트의 모든 class component는 React.Component를 상속 받는다.
        
        ```jsx
        class Welcome extends React.Component {
        	render() {
        		return <h1>안녕, {this.props.name}</h1>;
        }
        ```
        

<aside>
💡 컴포넌트의 이름은 항상 대문자로 시작해야 한다!
 - 리액트는 소문자로 시작하는 컴포넌트를 DOM 태그로 인식하기 때문

</aside>

```jsx
const element = <Welcome name ="세빈" />;
//welcome과 같이 소문자로 시작할 경우 리액트는
//이것을 dom 태그로 인식한다. 
```

- 컴포넌트 합성: 여러 개의 컴포넌트를 합쳐 또 다른 컴포넌트를 만드는 것
- 컴포넌트 추출: 복잡한 컴포넌트를 여러 개의 새로운 컴포넌트로 나누는 것

 - 컴포넌트의 재사용성이 올라감 → 컴포넌트가 작아질 수록 해당 컴포넌트의 기능과 목적이 명확해지고, props도 단순해짐

 - 개발속도가 올라감

<aside>
💡 어느정도 수준까지 추출하는가? 정해진 기준은 없음.
But 기능 단위로 구분하는 것이 좋고, 나중에 곧바로 재사용이 가능한 형태로 추출하는 것이 좋다.

</aside>

- 리액트로 만들어진 에어비앤비 사이트

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/bc137143-329d-42d8-abf2-0163d09f83a2/Untitled.png)

## Props

### Props의 특징

- Read-Only → 읽기 전용
    
    리액트 엘리먼트의 특징이 불변성 → Props는 리액트 컴포넌트가 엘리먼트를 생성하기 위해 사용하는 값이다.  이 값이 엘리먼트 생성도중 변한다면 제대로 된 엘리먼트 생성이 불가하다.
    

### Props사용법

- jsx의 경우

```jsx
function Hello(props){
		return (
				<Profile
						name = "은택"
						introduction = "22학번 응소입니다."
						account = {250,000}
				/>
    );
}
```

: key와 value값으로 이루어진 키, 값의 형태로 props를 사용할수있음.

<aside>
💡 **value값중 “”와 {}의 차이는 무엇일까?**

jsx코드에서 {}안에는 js코드가 들어간다. 문자열 이외의 정수,변수, 다른 컴포넌트를 넣을때에는 중괄호로 감싸야함

</aside>

후에 profile 컴포넌트로 Props가 이동하고

```jsx
{
		name = "은택"
		introduction = "22학번 응소입니다."
		account = {250,000}
}
```

Props는 이와같이 js의 객체가 됨.

- Props에 중괄호를 사용해서 아래와같은 컴포넌트도 넣을 수 있음.

```jsx
header={
    <Header title="hi" />
}
```

- jsx를 사용하지 않는경우 Props를 추가하는 방법 →리액트의 createElement함수를 통해서 추가한다.

```jsx
React.createElement(
		type,
		[Props],
    [...children]
)
//Props에 자바스크립트 객체를 추가하면 그게 해당 컴포넌트의 props가됨
```

## State

- 리액트 컴포넌트의 상태를 의미한다. (리액트의 컴포넌트의 변경가능한 데이터)
- 쇼핑몰에서 물건 수량을 입력하거나, 상품에 댓글을 남기는 등 상태를 바꿔야하는 경우 사용한다. (+ 버튼을 클릭하거나 값을 입력하는 등의 이벤트와 함께 사용된다! )
- 렌더링이나 데이터 흐름에 사용되는 값만 state에 포함시켜야 한다.
- 주의 사항
    - 생성자 (constructor)에서 반드시 초기화 해야 한다.
    
    ```jsx
    import React from 'react';
    
    class SebinExample extends React.Component {
    	constructor(porps) {  // 맨 처음 생성될 때 한 번만 호출.
    		super(props);       
    		this.state = {
    			name: 'sebin',
    		};
    	}
    	...
    }
    ```
    
    - state를 직접 수정할 수 없다.  setState() 함수를 활용하여 수정한다.
    
    ```jsx
    this.state = {
    	name: 'sebin'
    };    //잘못된 수정 방법
    ```
    
    ```jsx
    this.setState = ({
    	name: 'sebin'
    });   // 올바른 수정 방법
    ```
    
    - setState() 함수는 비동기로 처리되며, setState() 코드 이후로 연결된 함수들의 실행이 완료된 시점에 화면 동기화 과정을 거친다.

## Lifecycle

- 리액트 컴포넌트의 생명주기 (컴포넌트가 생성되는 시점과 사라지는 시점이 정해져 있다는 의미이다.)

![Lifecycle.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/5f02df57-d352-4cc2-a951-ee12ebc86114/Lifecycle.png)

- 생명주기에 따라 호출되는 클래스 컴포넌트의 함수들
- componentDidMount
- componentDidUpdate
- componentWillUnmount
→ 생명 주기 함수들(LifeCycleMethod)

- 출생(Mounting): 컴포넌트가 생성되는 시점
- 컴포넌트의 constructor가 실행됨(컴포넌트의 state를 정의) → 렌더링 → componentDidMount 실행

- 인생(Updating): 렌더링을 여러번 하는 과정(props가 변경되거나, setState()를 통해 state가 변경되거나, forceUpdate()(강제 업데이트 함수)를 통해 컴포넌트가 다시 렌더링된다.

- 사망(Unmounting): 상위 컴포넌트에서 현재 컴포넌트를 더 이상 표시하지 않을 때
- componentWillUnmount 실행

<aside>
💡 component는 계속 존재하는 것이 아니라, 시간의 흐름에 따라 생성되고 업데이트 되다가 사라진다.

</aside>

[React 시작하기 - Web 개발 학습하기 | MDN](https://developer.mozilla.org/ko/docs/Learn/Tools_and_testing/Client-side_JavaScript_frameworks/React_getting_started)
