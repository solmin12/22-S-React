## react Component

:입력(props: 속성)에 따라 정해진 출력(React Element: react App을 구성하는 가장 작은 Building block)을 반환

- 하나의 컴포넌트를 반복적으로 사용하는 개발 방식→전체 코드량을 줄이고, 개발 시간 및 유지 보수 비용 절약
- 객체지향의 Class 및 Instance와 동일하진 않으나 유사한 개념으로 이해 가능
- Component는 Class와 같은 역할을 하기때문에 실제로 rendering되는 것은 Component를 통해 만들어진 Element에 해당

### Component의 합성과 추출

- react의 구조는 컴포넌트 기반의 구조로서, 하나의 컴포넌트는 여러개의 컴포넌트의 조합으로 구성 가능 = Component 합성
- 복잡한 component를 쪼개어 여러개의 component로 분리가능=Component 추출

<aside>
💡  장점
- 재사용성 증가 : component가 작아질수록, 해당 component의 기능과 목적이 명확해지고, 단순해짐
- 개발 속도 단축 : 재사용성 증가에 따른 자연스러운 현상

Component는 기능 단위로 추출하는 것을 권장

곧바로 재사용이 가능한 형태로 추출하는 것을 권장

</aside>

### Component작명 주의사항

- 항상 대문자로 시작

<aside>
💡 - react는 소문자로 시작하는 태그를 DOM tag로 인식
- 대문자로 시작하는 태그는 JS내에서 사용자가 정의 및 Import한 Component로 인식

</aside>

```jsx
//HTML div태그로 인식
const element=<div />;
//React Component로 인식
const element=<Div name="div" />;
```

### Function Component 함수 컴포넌트

- 간단한 코드를 갖는다는 장점

### Class Component 클래스 컴포넌트

- JS ES6의 class를 사용해서 만들어진 형태의 Component
- React.Component를 상속받아서 만들어짐

## Props

: React Component의 input

- property의 줄인 것으로 react Component의 속성을 의미함
- Component에 전달할 다양한 정보를 담고 있는 JS객체

### 특징

- 읽기 전용 특징

<aside>
💡 Props는 react component가 element를 생성하기위해 사용하는 것으로 element생성 도중 변경되는 것을 금지 

따라서 다른 값으로 element를 생성하고 싶은 경우에는 새로운 값을 Props로 Component에 전달하여 새로 element를 생성 →Element Rerendering

</aside>

- Props에게 Component란 Pure함수 역할 →react component가 Props를 직접 바꿀 수 없고 같은 Props에 대해서 항상같은 element를 반환

<aside>
💡 JS 특징
- Pure
: input을 변경하지 않으며, 같은 input에 대해서는 항상 같은 output
- Impure
: input을 변경시킴

</aside>

## state

: react Component의 변경 가능한 data

- React Component를 개발하는 개발자가 정의
- 렌더링이나 데이터 흐름에 사용되는 값만 state에 포함시켜야함

<aside>
💡 state 변경시 Component 재랜더링 발생→ 랜더링과 data흐름에 관련없는 값을 포함시킨다면 불필요한 재랜더링으로인한 성능저하

관련 없는 값→ Component의 인스턴스 필드로 정의

</aside>

- state는 JS객체이다.

```jsx
//Button이라는 React Component
class Button extends React.Component{
constructor(props){//생성자로서 class가 생성될 때 실행
super(props);

this.state={//현재 Component의 state를 정의
     liked :false
      };
   }
..
}

**//class Component는 state를 생성자에서 정의
//함수형 Component는 state를 useState Hook을 사용해서 정의**
```

- 직접수정 방식을 지양 → setState함수 사용을 권장

```jsx
//권장 수정 방식
this.setState({
        name : 'Inje'
});
```

<aside>
💡 더불어 react의 state는 component의 랜더링과 관련되어, 수정 방식을 따르지 않으면 개발자가 의도하지 않은 방식의 작동 가능성 존재

</aside>

## Lifecycle

: 생명주기 Mounting→Updating→Unmounting(life cycle method)

- component가 계속 존재하지 않음
- 시간의 흐름에 따라 생성되고 업데이트 되다가 사라지는 과정

### Mounting : component의 생성시점

1. constructor(생성자) 실행단계 →component의 state정의
2. Component rendering
3. componentDidMount 함수 호출

### Updating : component의 update과정

1. update 과정
- Component props변경
- setState()→state변경
- forceUpdate() : 강제 업데이트 함수→ Component 재랜더링
1. componentDidUpdate 함수 호출

### Unmounting : component의 사망시점

:상위 Component에서 현재 Component를 더 이상 화면에 표시하지 않을 때 Unmount되었다고 표현

1. unmount직전에 componentWillUnmount함수 호출