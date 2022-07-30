# <State and Lifecycle>

## State

- 리액트에서 state → 리액트 컴포넌트의 상태

- 정상, 비정상인지를 나타내는 것인지보다 리액트 컴포넌트의 변경가능한 데이터를 의미한다.

- 사전에 미리 정해진 것이 아니라, 리액트 컴포넌트를 개발하는 개발자가 직접 정의해서 사용

- 꼭 렌더링이나 데이터 흐름에 사용되는 값만 state에 포함시켜야 함! (state가 변경될 경우, 컴포넌트가 다시 렌더링 되기 때문에 성능을 저하시킬 수 있음) → 렌더링이나 데이터 흐름에 사용되지 않는 값: 컴포넌트에 인스턴스빌드로 정의하면 됨

<aside>
💡 state는 자바스크립트의 객체이다!

</aside>

예제코드)

```jsx
class LikeButton extends React.Component{
	constructor(props){
		super(props);
		this.state={
			liked: false
		};
	}
...
}
```

 - 모든 클래스 컴포넌트에는 constructor(=생성자)라는 함수를 가지고 있는데, 클래스가 생성될 때 실행되는 함수이다.

- state는 정의된 이후 일반적인 js 변수를 다루듯이 직접 수정할 수 없다. → (엄밀히)수정이 가능하지만 수정해서는 안된다.

```jsx
//state를 직접 수정 (잘못된 사용법)
	this.state={
		name='hyunjin'
	};

//setState 함수를 통한 수정 (정상적인 사용법)
 this.setState({
		name='hyunjin'
	});
```

 - state를 수정하고자 할 때에는 꼭 setState 함수를 사용해야만 한다.

## Lifecycle

- 리액트 컴포넌트의 생명주기 (컴포넌트가 생성되는 시점과 사라지는 시점이 정해져 있다는 의미)

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
💡 component가 계속 존재하는 것이 아니라, 시간의 흐름에 따라 생성되고 업데이트 되다가 사라진다.

</aside>

## React Developer Tools

- 크롬 확장 프로그램
- 개발자모드 누르면 components, profile이라는 새로운 탭이 생성 
- components 탭 → 현재 화면에 존재하는 컴포넌트가 트리 형태로 보임. 각 컴포넌트 별로 props와 state도 확인 가능

- profiler 탭 → 어떤 컴포넌트가 렌더링 되었는지, 렌더링 시간은 얼마나 소요하였는지, 컴포넌트가 왜 다시 렌더링 되었는지를 확인할 수 있음 
   ~> 불필요하게 렌더링되거나 무거운 컴포넌트를 찾아 최적화함으로써 리액트 app의 성능을 향상시킬 수 있다.