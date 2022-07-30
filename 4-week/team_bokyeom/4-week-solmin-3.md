# 2022.7.29 Cow 프론트엔드 공부

---

- [x]  인프런 React 강의 Section8
- [x]  추가 자료조사(binding)

---

Handling Events

Event(사건) 특정 사건을 의미함 (ex 버튼을 클릭하는 이벤트), 이러한 Event를 다루는 것을 Handling한다 함

```jsx
//DOM의 Event
<button onclick="activate()">
	Active
</button>
```

DOM의 Event는 onclick을 통해 클릭 이벤트를 처리하고 문자열로 active()라는 함수를 넣음

```jsx
//React의 Event
<button onClick={activate}>
	Activate
</button>
```

React의 Event는 onClick(camelCase)을 통해 클릭 이벤트를 처리하고 처리할 함수를 함수 그대로 전달함

DOM과 React의 Event 차이점

- Event이름의 표기법이 다름
- 함수를 전달하는 방식이 다름

<aside>
💡 camelCase란?
카멜(낙타) 표기법이라 부름
낙타의 혹처럼 오르락 내리락 하는 영어표기법

</aside>

Event Handler

- Event를 다루는 함수
- Event Listener라고 부르기도 함

bind?

binding을 사용하는 이유

- 객체 메서드를 Callback으로 전달할 때 ‘this 정보’가 사라지는 문제를 해결하기 위함

<aside>
💡 this정보가 사라진다?
객체 메서드가 객체 내부가 아닌 다른 곳에 전달되어 호출되면 this가 사라짐

</aside>

```jsx
//user.sayHi를 호출할 경우 'Hello, John!'이 출력되어야 하나 undefined가 출력됨
let user = {
  firstName: "John",
  sayHi() {
    alert(`Hello, ${this.firstName}!`);
  }
};

setTimeout(user.sayHi, 1000); // Hello, undefined!
//객체에서 분리된 함수인 user.sayHi가 전달되기 때문
```

모든 함수는 this를 수정하게 해주는 내장 메서드 bind를 제공

```jsx
//기본문법
let boundFunc = func.bind(context);
```

[함수 바인딩](https://ko.javascript.info/bind)

[Function.prototype.bind() - JavaScript | MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_objects/Function/bind)

Arguments전달하기

Argument(주장)

- 함수(Event Handler)에 전달할 데이터

Parameter

- 매개변수

```jsx
//Class Component의 경우
//Arrow Function
<button onClick={(event) => this.deleteItem(id, event)}>삭제하기</button>
//bind
<button onClick={this.deleteItem.bind(this, id)}>삭제하기</button>
```

event라는 매개변수는 React의 Event객체를 의미

첫 번째 매개변수로 id, 두 번째 매개변수로 event가 전달됨

Arrow Function은 명시적으로 두 번째 매개변수로 event를 넣은 반면, bind의 경우 두 번째 매개변수로 event가 자동으로 들어감

```jsx
//Function Component의 경우
function MyButton(props){
	const handleDelete = (id, event) => {
		console.log(id, event.target);
	};

	return (
		<button onClick={(event) => handleDelete(1, event)}>
			삭제하기
		</button>
	);
}
```