# React

# Rendering Elements

## Elements

- react elements : react의 virtual DOM에 존재하는 elements
- DOM elements : 실제 브라우저의 DOM에 존재하는 elements

## React Elements

: React를 구성하는 가장 작은 블록

- 화면에서 보이는 것들을 기술
- Component유형과 속성 및 내부의 모든 자식에 대한 정보를 저장하고 있는 일반적인 JS객체 형태로 존재
- 불변성(한번 생성되면 변경 불가) 갖음 → 갱신이 필요한 경우 해당 위치의 element를 새로 만든 element로 바꿔치기함

```jsx
//element
{
type : 'button', //해당 tag를 갖는 DOM node
   props : { //sytle및 class등의 속성
        className:'one'
        children: {
            type: 'b',
            props:{
            children: 'Hello, element!'
                   }
             }
      }
}

//React Component Element
{
type : Button,//react component의 이름
   props : {
       color:'red',
       children : 'Hello'       
       }
}
```

## rendering

: React Elements가 virtual DOM에서 실제 브라우저의 DOM으로 이동하는 과정

- rendering을 위해서는 ReactDOM의 render(react element, DOM Element)함수를 사용

```jsx
const element : <h1>안녕</h1>;
ReactDOM.render(element,document.getElementById('root'));
```