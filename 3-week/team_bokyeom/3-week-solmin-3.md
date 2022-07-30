# 2022.7.23 Cow 프론트엔드 공부

---

- [x]  인프런 React 강의 Section5~6

---

Components(구성요소) and Props(변수)

Componenet

작은 component가 모여 큰 component를 구성하고 이런 component가 모여 하나의 페이지를 구성

React component도 입력을 받아 정해진 출력을 내뱉음

어떠한 속성들을 입력으로 받아 그에 맞는 element를 생성하여 return

ex) Component라는 붕어빵 틀에서 Element라는 붕어빵을 생성

Props(Property/속성)

- Component의 속성

ex) 붕어빵에 들어가는 재료(팥,슈크림,고구마)

- Component에 전달할 다양한 정보를 담고 있는 자바스크립트 객체
- 특징
1. Read-Only(읽기전용)
- 값을 변경 할 수 없다
2. 모든 리액트 component는 props를 직접 바꿀 수 없고 같은 props에 대해서는 항상 같은 결과를 보여줄것!

JavaScript함수의 속성

```jsx
function sum(a,b){
	return a+b;
}
//pure하다
```

입력값(input)을 변경하지 않으며, 같은 입력값에 대해서는 항상 같은 출력값(output)을 리턴

```jsx
function withdraw(account, amount){
	account.total -= amount;
}
//Impure하다
```

입력으로 받은 값을 변경함

Props 사용법

JSX를 사용할 경우

```jsx
function App(props){
	return (
		<Profile
			name="소플"
			introduction="안녕하세요, 소플입니다."
			viewCount={1500}
		/>
	);
}
```

JSX를 사용하지 않을 경우

```jsx
React.createElement(
	Profile,
	{
		name: "소플",
		introduction: "안녕하세요, 소플입니다.",
		viewCount: 1500
	},
	null
);
```

Component만들기

- Function Component

```jsx
function Welcome(props){
	return <h1>안녕, {props.name}</h1>;
}
```

- Class Component

```jsx
class Welcome extends React.Component{
	render(){
		return <h1>안녕, {this.props.name}</h1>;
	}
}
```

Component의 이름

- 항상 대문자로 시작해야 함
- React는 소문자로 시작하는 Component를 DOM으로 인식

HTML div 태그로 인식

```jsx
const element = <div />;
```

Welcome이라는 React Componenet로 인식

```jsx
const element = <Welcome name="인제" />;
```

Component 렌더링

```jsx
function Welcome(props){
	return <h1>안녕, {props.name}</h1>;
}

const element = <Welcome name="인제" />;
ReactDOM.render(
	element,
	document.getElementById('root)
);
```

Component합성

- Component안에 Component 생성 가능

```jsx
function Welcome(props){
	return <h1>Hello, {props.name}</h1>;
}
function App(props) {
	return (
		<div>
			<Welcome name="Mike" />
			<Welcome name="Steve" />
			<Welcome name="Jane" />
		</div>
	)
}

ReactDOM.render(
	<App />,
	document.getElementById('root')
);
```

Component 추출

- 재사용성이 올라감
- Component가 작아질 수록 기능과 목적이 명확해지고 props도 단순해지기 때문

```jsx
function Comment(props) {
	return(
		<div ClassName="comment">
			<div ClassName="user-info">
				<img className="avatar"
					src={props.author.avatarUrl}
					alt={props.author.name}
				/>
				<div className="user-info-name">
					{props.author.name}
				</div>
			</div>

			<div className="comment-text">
				{props.text}
			</div>

			<div className="comment-date">
				{formatDate(props.date)}
			</div>
		</div>
	);
}
```

Avatar 추출하기

```jsx
function Avatar(props){
	return(
		<img className="avatar"
			src={props.user.avatarUrl}
			alt={props.user.name}
		/>
	);
}
```

```jsx
<img className="avatar"
					src={props.author.avatarUrl}
					alt={props.author.name}
/>

//변경
<Avatar user={props.author} />
```

UserInfo 추출하기

```jsx
function UserInfo(props){
	return(
		<div className="user-info">
			<Avatar user={props.user} />
			<div className="user-info-name">
				{props.user.name}
			</div>
		</div>
	);
}
```

```jsx
<div ClassName="user-info">
	<img className="avatar"
		src={props.author.avatarUrl}
		alt={props.author.name}
	/>
	<div className="user-info-name">
		{props.author.name}
	</div>
</div>

//변경
<UserInfo user={props.author} />
```
기능 단위로 구분하고 곧바로 재사용이 가능한 형태로 추출하는 것이 좋음

State(상태)

- React Component의 변경 가능한 데이터
- 렌더링이나 데이터 흐름에 사용되는 값만 state에 포함시켜야 함
- JavaScript 객체
- 직접 수정 할 수 없음

```jsx
//state를 직접 수정 (잘못된 사용법)
this.state = {
	name: 'Inje;
};

// setState 함수를 통한 수정 (정상적인 사용법)
this.setState({
	name: 'Inje'
});
```

Lifecycle(생명주기)

- Component가 생성되는 시점과 사라지는 시점이 정해져 있음
- Mounting - Updating - Unmounting
- Component는 계속 존재하는 것이 아니라, 시간의 흐름에 따라 생성되고 업데이트 되다가 사라짐