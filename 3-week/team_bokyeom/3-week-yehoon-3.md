# Component/props

![Untitled](Component%20props%20e6141409de6846a79ee3c6c8601c2066/Untitled.png)

**Component가 붕어빵 틀이라면 Element는 그 틀로 만들어진 다양한 붕어빵들을 의미한다.**

**props는 property(속성)를 의미한다.** 

**더 정확히 말하자면 Component에 전달할 다양한 정보를 담고 있는 자바스크립트 객체이다.**

![Untitled](Component%20props%20e6141409de6846a79ee3c6c8601c2066/Untitled%201.png)

**Props는 속재료라고 생각하면 된다. Props에 따라서 다양한 element가 생성된다.**

**ex)**

![Untitled](Component%20props%20e6141409de6846a79ee3c6c8601c2066/Untitled%202.png)

**위에 빨간 테투리로 되어있는 부분은 같은 component이다.**

**그러나 props가 다르기 때문에 모두 각각 다른 element이다.**

## props 특성

**값을 변경할 수 없다.  (이미 붕어빵을 다 만들어놓은 상태에서 속재료를 변경할 수 없다고 생각하면 된댜.)**

### **그렇다면 어떻게 해야하나!?**

**새로운 값을 Component에 전달하여 새로운 element를 생성하면 된다.**

## ★모든 리액트 컴포넌트들은 그들의 props에 관해서는 pure 함수 같은 역할을 해야한다.

# **→ 모든 리액트 Component는 props를 직접 바꿀 수 없고, 같은 props에 대해서는 항상 같은 결과를 보여야한다.**

![Untitled](Component%20props%20e6141409de6846a79ee3c6c8601c2066/Untitled%203.png)

**Component의 종류에는 함수 component와 클래스 component가 있다.**

**★Component를 생성할 때 주의해야 할 점!**

- Component의 이름은 항상 대문자로 시작해야 한다.
- 만약 소문자로 시작한다면 Component로 인식하지 않을 수 있다.

## Component 합성

- **Component 안에 또 다른 Component를 쓸 수 있다.**
- **복잡한 화면을 여러 개의 Component로 나눠서 구현 가능하다는 장점이 있다.**

![Untitled](Component%20props%20e6141409de6846a79ee3c6c8601c2066/Untitled%204.png)

![Untitled](Component%20props%20e6141409de6846a79ee3c6c8601c2066/Untitled%205.png)

## Component 추출

- **큰 Component를 산산조각 내는 것을 의미한다.**
- **재사용성이 높아진다.**
- **개발 속도가 빨라진다.**

![Untitled](Component%20props%20e6141409de6846a79ee3c6c8601c2066/Untitled%206.png)

![Untitled](Component%20props%20e6141409de6846a79ee3c6c8601c2066/Untitled%207.png)

![Untitled](Component%20props%20e6141409de6846a79ee3c6c8601c2066/Untitled%208.png)

## State

- **State는 리액트 Component의 데이터 상태를 의미한다.**
- **State는 개발자가 정의한다.**
- **렌더링이나 데이터 흐름에 사용되는 값만 State에 포함시켜야 한다.**
- **State는 자바스크립트의 객체이다.**
- **State는 직접 수정하면 안된다.**

## Lifecycle

- **리액트 Component의 생명주기를 말한다.**
- **Component는 계속 존재하는 것이 아니라, 시간의 흐름에 따라 생성되고 업데이트 되다가 사라진다.**

![Untitled](Component%20props%20e6141409de6846a79ee3c6c8601c2066/Untitled%209.png)