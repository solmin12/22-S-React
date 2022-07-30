# 7/22일 학습 내용

## JSX , Element , CreateElement , Virtual DOM

![Untitled](7%2022%E1%84%8B%E1%85%B5%E1%86%AF%20%E1%84%92%E1%85%A1%E1%86%A8%E1%84%89%E1%85%B3%E1%86%B8%20%E1%84%82%E1%85%A2%E1%84%8B%E1%85%AD%E1%86%BC%2069587ea6267c455aa3a204a2528f8b61/Untitled.png)

Element는  실제로 화면에 렌더링 할 DOM 노드들의 정보를 React에게 알려주기 위한 수단이다.

React JS로 Element를 생성하는 방법 1. CreateElement

React.createElement라는 함수를 사용하여 Element를 생성하는 거다 

```jsx
const span=React.createElement("span");

ReactDOM.render(span, root);

/*루트라고 적은 이유는 보통 html에 일반적으로 
<div id="root"><div> 선언하고 자바스크립트에
const root=document.getElementById("root");
라고 생성하기에 body에 들어간다 생각하면 편하다*/
```

그럼 이렇게 react elements가 생성되면 위 사진과 같이 virtual dom에 생성된것이고 render함수를 통해 DOM Elements로 element를 렌더링한다 (react element는 저 원이라고 생각하면 편하다)

React JS로 Element를 생성하는 방법 2.JSX

HTML문법과 유사해 createElement보다 jsx를 더 많이 사용한다 

```jsx
const Title =(<h3>제목입니다</h3>);

ReactDOM.render(Title,root);
```

JSX문법은 브라우저가 알지못하기에 createElement 형식으로 변환되는데 이걸 자동으로 해주는 것이 Babel(컴파일러)이다

JSX또한 render함수를 통해 DOM elements에 렌더링 된다

변경사항이 있을 때

**element는 한번 생성이 되면 수정할 수 없다**. 그렇기에 업데이트,변경사항이 생기면 속도가 훨씬 빠른 Virtual DOM에서 수정 사항을 체크하고 그 수정사항이 있는 Element들을 업데이트하는 것이 아니라 새로 생성하고 생성된 Element들로 변경해준다.

component와 element는 붕어빵과 붕어빵 틀이라고 생각 붕어빵은 한번 생성하면 못 바꾸니까

참고자료: [https://velog.io/@ohk9134/React-기초-React-사용-목적-createElement-JSX-Babel](https://velog.io/@ohk9134/React-%EA%B8%B0%EC%B4%88-React-%EC%82%AC%EC%9A%A9-%EB%AA%A9%EC%A0%81-createElement-JSX-Babel)

[https://moonsbeen.tistory.com/258](https://moonsbeen.tistory.com/258)

[https://velog.io/@97godo/React-Element-와-DOM-Element-Component-Element](https://velog.io/@97godo/React-Element-%EC%99%80-DOM-Element-Component-Element)

렌더링 업데이트

불변성으로 인해 렌더링하기 위해선 element를 다시 생성해야한다

```jsx
function tick(){
const element=(
<div>
<h1>안녕 리액트!</h1>
<h2>현재 시간:{new Date().toLocaleTimeString()}
</h2><div>);
ReactDOM.render(element,
document.getElementById('root'));
}
setInterval(tick,1000);
```

이 코드는 1초마다 tick이라는 함수가 실행되는데 element는 함수가 실행될때마다 새롭게 생성되는 것이다

## Component

component란?

프로그래밍에 있어 재사용이 가능한 독립된 모듈을 뜻한다

레고 블록처럼 만들어진 컴포넌트들을 조합하여 화면을 구성할 수 있다

또한 함수가 입력을 받아서 출력을 내뱉는 것처럼 컴포넌트도 입력을 받아서 출력을 내뱉는다 하지만 입력은 prop로 입력을 해서 출력은 react element가 된다.

ex)element들로 구성된 react element가 있고 이 element를 만들어내는 틀을 component라고 생각하면 편하다 붕어빵을 element , 붕어빵틀을 component라고 생각할 수도 있다 (클래스와 인스턴스 개념으로 생각할 수도 있다)

ex) 에어비앤비 사이트는 리액트로 만든 사이트이다 밑에 그림을 보면 훨씬 이해하기 편하다

![Untitled](7%2022%E1%84%8B%E1%85%B5%E1%86%AF%20%E1%84%92%E1%85%A1%E1%86%A8%E1%84%89%E1%85%B3%E1%86%B8%20%E1%84%82%E1%85%A2%E1%84%8B%E1%85%AD%E1%86%BC%2069587ea6267c455aa3a204a2528f8b61/Untitled%201.png)

component의 장점 , 특징

재사용성이라는 가장 큰 강점을 가지고 있어 개발 시간을 줄여주고 유지보수에 좋다.

또한 컴포넌트 안에 컴포넌트가 있을수도 있고 모든 리액트는 컴포넌트로 구성되어있다고 볼 수 있다

## component의 종류

함수형 컴포넌트

function으로 정의하고 return 문에 jsx 코드를 반환한다

이때 함수형 컴포넌트는 function을 사용하지 않고 화살표 함수로 정의해도 된다 

```jsx
function NameBox(){
const name="test";
return <div>{name}</div>;
}  //함수형 컴포넌트

const NameBox=()=>{
const name="test";
return <div>{name}</div>;
} //화살표 함수로 정의한 컴포넌트
```

클래스형 컴포넌트 

클래스로 정의하고 render()함수에서 jsx 코드를 반환한다.

클래스형 컴포넌트는 hook이 등장한 이후부터 잘 사용안한다 

```jsx
class NameBox extends React.Component{
render(){
const name="react";
return <div className="react">{name}</div>
}
}
```

컴포넌트 추출

큰 컴포넌트를 조각내서 작은 컴포넌트로 만들기 가능 이러면 재사용성으로 개발 속도가 향상된다

주의사항

컴초넌트는 항상 대문자로 시작해야한다 소문자로 시작하면 DOM태그로 인식하기 때문이다

## Props

 

props란?

props는 속성으로 컴포넌트에 전달할 다양한 정보를 담고 있는 객체이다.

ex) 위에 붕어빵 예시가 있으면 붕어빵에 들어갈 재료를 의미한다고 생각

props의 특징

값을 변경할 수 없다(붕어빵이 다 구워졌는데 속재료를 바꿀 수 없는 것 처럼)다른 props의 값을 만들려면 새로운 값을 컴포넌트에 전달하여 새로 element를 생성해야한다

모든 리액트 컴포넌트는 props를 직접 바꿀 수 없고 같은 props에 대해서는 항상 같은 결과를 보여줘야한다 ( 항상 같은 결과를 보여주기 위해서는 컴포넌트 안에서 props의 속성을 바꾸는 작업을 할 수는 없다)

props는 중괄호를 사용하고 중괄호는 자바스크립트 코드라고 생각하면 된다

```jsx
//Hello.js

function Hello(props){
return <div>안녕하세요 {props.name}</div>
}

//App.js
import Hello from './Hello';
function App(){
return(<Hello name="react"/>
);
}
```

props 비구조화 할당 (구조 분해)

```jsx
function Hello(props){
return <div style={{ color:props.color}}>
안녕하세요 {props.name}</div>
} 

//위 함수를 밑에 함수컴포넌트 처럼 작성해서
//조금 더 간결하게 만들 수 있다

function Hello({color,name}){
return <div style={{color}}>인녕하세요 {name}</div>
}
```

defaultProps로 기본 값 설정

컴포넌트에 props를 지정하지 않았을 때 기본적으로 사용할 값을 설정해주기 위한 목적이다

참고자료

[https://react.vlpt.us/basic/05-props.html](https://react.vlpt.us/basic/05-props.html)

[https://hanamon.kr/컴포넌트-component란/](https://hanamon.kr/%EC%BB%B4%ED%8F%AC%EB%84%8C%ED%8A%B8-component%EB%9E%80/)

[https://moonsbeen.tistory.com/258](https://moonsbeen.tistory.com/258)

[https://chanhuiseok.github.io/posts/react-4/](https://chanhuiseok.github.io/posts/react-4/)