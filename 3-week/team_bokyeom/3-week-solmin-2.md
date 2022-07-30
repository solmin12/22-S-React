# 2022.7.20 Cow 프론트엔드 공부

---

- [x]  인프런 React 강의 Section3~4

---

JSX(A syntax extension to JavaScript)(자바스크립트의 확장문법)

JavaScript + XML/HTML

JSX코드 예시

```jsx
const element = <h1>Hello, world!</h1>.;
```

React.creatElement()함수

→XML/HTML코드를 JavaScript코드로 변환

createElement()함수의 변수

```jsx
React.createElement(
		type,
		[props],
		[...children]
)
```

type = HTML tag나 다른 React Component

props = 속성들

children = 현재 element가 포함하고 있는 자식코드

장점

1. 간결한 코드
2. 가독성 향상
3. Injection Attacks 방어 - 보안성 높음

사용법

…XML/HTML + {JavaScript}

```jsx
function getGreeting(user){
	if (user){
		return <h1>Hello, {formatName(user)}!</h1>;
	}
	return <h1>Hello, Stranger.</h1>
}
```

태그의 속성(attribute)에 값을 넣는 방법

```jsx
//큰따옴표 사이에 문자열을 넣거나
const element = <div tabIndex="0"></div>;

//중괄호 사이에 자바스크립트 코드를 넣으면 됨!
const element - <img src={user.avatarUrl}></img>;
```

자식(children)을 정의하는 방법

```jsx
cosnt element = (
	<div>
		<h1>안녕하세요</h1>
		<h2>열심히 리액트를 공부해 봅시다!</h2>
	</div>
);
```

Redndering Elements

Elements란?

영어 뜻 : 어떤 물체를 구성하는 성분

Elements are the smallest building blocks of React apps.

리액트 앱을 구성하는 가장 작은 빌딩 블록들

화면에 나타나는 내용을 기술하는 자바스크립트 객체 - Element

![화면 캡처 2022-07-20 131433.png](2022%207%2020%20Cow%20%E1%84%91%E1%85%B3%E1%84%85%E1%85%A9%E1%86%AB%E1%84%90%E1%85%B3%E1%84%8B%E1%85%A6%E1%86%AB%E1%84%83%E1%85%B3%20%E1%84%80%E1%85%A9%E1%86%BC%E1%84%87%E1%85%AE%20ca5c7e7a0dce4d518d8f1759d95589a2/%25ED%2599%2594%25EB%25A9%25B4_%25EC%25BA%25A1%25EC%25B2%2598_2022-07-20_131433.png)

React Elements는 화면에서 보이는 것들을 기술

React Elements는 자바스크립트 객체 형태로 존재

특징

1. 불변성(immutable)
- element 생성 후에는 children이나 attribute를 바꿀 수 없다