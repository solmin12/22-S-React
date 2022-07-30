# Hooks
### component
1. function component
- state 사용 불가 
- Lifecycle에 따른 기능 구현 불가

2. class component 
- 생성자에서 state 정의 
- setState() 함수를 통해 state 업데이트
- Lifecycle methods 제공

function component를 보완하기 위해 생성된 것이 Hooks
원래 존재하는 어떤 기능에 갈고리를 끼우는 것처럼 연결시키는 것을 의미한다

### useState()
- state를 사용하기 위한 Hook
- const [변수명, set함수명] =useState(초깃값)을 입력하여 사용한다.

예시
```jsx
import React, {useState} from "React";
function Counter(props){
	const [count, setCount] = useState(0);
	return (
	<div>
		<p> 총 {count}번 클릭했습니다.</p>
		<button onClick={ ( ) => setCount (count + 1)}>
			클릭
		</button>
	</div>
	);
}
```

### useEffect()
- Side Effect를 사용하기 위한 Hook
- 리액트에서 side Effect는 효과, 영향을 의미
- 사용하는 이유는 작업들이 다른 component에 영향을 미칠 수 있어, 렌더링 중에는 작업이 완료될 수 없기 때문

useEffect() 사용법
```jsx
useEffect(이펙트 함수, 의존성 배열)
```
- Effcet function이 mount, unmount 시에 단 한 번씩만 실행된다

```jsx
useEffect(이펙트 함수, [ ]);
```
- 의존성 배열을 생략하면 컴포넌트가 업데이트될 때마다 호출된다

```jsx
useEffect(이펙트 함수);
```
- useEffect( )의 return은 컴포넌트가 Unmount 될 때 호출된다

### useMemo()
- Memoized value를 반환하는 Hook

Memoization
- 연산량이 많이 드는 함수의 호출결과를 저장해 두었다가 같은 입력 값으로 함수를 호출하면 새로 함수를 호출하지 않고 저장해놨던 호출결과를 반환시킴
- 걸리는 시간 단축, 불필요한 중복연산 X, 빠른 렌더링 속도

useMemo() 사용법
```jsx
const memoizedValue = useMemo(
	() => {
		//연산량이 높은 작업을 수행해 결과를 반환
		return computeExpensiveValue(의존성 변수1, 의존성 변수2);
	},
	[의존성 변수1, 의존성 변수2]
);
```
- useMemo()로 전달된 함수는 렌더링이 일어나는 동안 실행됨
- 즉, 렌더링이 일어나는 동안에 실행되어서는 안 될 작업을 useMemo() 함수에 넣으면 안됨 => useEffect() Hook을 사용
- 의존성 배열을 넣지 않을 경우, 매 렌더링마다 함수가 실행됨
- 의존성 배열이 빈 배열일 경우, 컴포넌트 마운트 시에만 호출됨

### useCallback()
- useMemo() Hook과 유사하지만 값이 아닌 함수를 반환
- 컴포넌트가 렌더링 될 때마다 매번 함수를 새로 정의하는 것이 아니라 의존성 배열의 값이 바뀐 경우에만 함수를 새로 정의해서 return

useCallback() 사용법
```jsx
const memoizedCallback = useCallback (
	( ) => {
		dosomething(의존성 변수1, 의존성 변수2);
	},
	[의존성 변수1, 의존성 변수2]
);
```
- 동일한 역할을 하는 두 줄의 코드  
useCallback(함수, 의존성 배열);  
useMemo( () => 함수, 의존성 배열);
- useCallback을 사용하지 않고 컴포넌트 내에서 정의하는 함수를 자식 컴포넌트의 props로 넘겨 사용하는 경우,  
 부모의 컴포넌트가 렌더링될 때마다 매번 자식 컴포넌트도 렌더링 됨
- useCallback인 경우 특정 변수의 값이 변한 경우에만 함수 정의됨

### useRef()
- Reference를 사용하기 위한 Hook
- Reference 객체를 반환
- Refence = 특정 컴포넌트에 접근할 수 있는 객체

useRef() 사용법
```jsx
const refContainer = useRef(초깃값);
```
- useRef( ) Hook은 내부의 데이터가 변경되었을 때 별도로 알리지 않는다
- 즉, current 속성을 변경한다 해서 재 렌더링이 되는 건 아니다
- Ref의 DOM 노드가 연결되거나 분리되었을 때 어떤 코드를 실행하고 싶다면 callBack ref를 사용한다

### Hook의 규칙
- Hook은 무조건 최상위 레벨에서만 호출해야 한다
- Hook은 컴포넌트가 렌더링될 때마다 매번 같은 순서로 호출되어야 한다
- Hook은 리액트 함수 컴포넌트에서만 Hook을 호출해야 한다

### eslint-plugin-react-hooks
- Hook의 규칙을 따르도록 강제해주는 플러그인
- 리액트 컴포넌트가 hook의 규칙을 따르는지 안 따르는지 분석하고  
의존성 배열이 잘못되어 있는 경우 고칠 방법을 제안함

### Custom Hook 
- 반복되는 로직을 하나로 묶어 재사용하기 위해 Custom Hook 생성
- 이름은 꼭 use로 시작하고 내부에서 다른 Hook을 호출하는 하나의 자바스크립트 함수
- 여러 개의 컴포넌트에서 하나의 Custom Hook을 사용할 때 컴포넌트 내부에 있는 모든 state와 effects는 전부 분리되어 있다.
- 각 Custom Hook 호출에 대해서 분리된 state를 얻게되고 Custom Hook 호출 또한 완전히 독립적이다

# Handling Events
### Event
- 특정 사건을 의미
- Ex) 사용자가 버튼을 클릭하는 사건 = 버튼 클릭 이벤트
- DOM과 React의 이벤트를 사용하는 방법이 조금 다르다  
Ex) Event 이름의 표기법과 함수를 전달하는 방식

### Event Handler 
- 어떤 이벤트가 발생하면 해당 이벤트를 처리하는 역할
- Event Listener 라고도 함

함수 컴포넌트에서 이벤트 핸들러 정의
```jsx
function Toggle(props) {
	const [isToggleOn, setIsToogleOn] = useState(true);
	// 방법 1. 함수 안에 함수로 정의
	function handleClick( ) {
		setIsToggleOn( (isToggleOn) => !isToggleOn);
	}
	
	// 방법 2. Arrow function을 사용하여 정의
	const handleClick = ( ) => {
		setIsToggleOn( (isToggleOn) => !isToggleOn);
	}
	return (
		<button onClick = { handleClick }>
			{isToggleOn ? “켜짐” : “꺼짐”}
		</button>
	);
}
```
### argument 전달
- argument는 함수에 전달할 데이터를 의미
- 즉, Event Handler에 전달할 데이터
- parameter 매개변수라고도 함
- 함수 컴포넌트에서 사용하며 매개변수 순서는 상관 X

### Quiz
1. Hook은 클래스 컴포넌트에서 호출 가능하다 (O/X)
2. useCallback() Hook이 useMemo() Hook과 유사하지만 다른 점은?