# Element

## 엘리먼트

엘리먼트는 React 앱의 가장 작은 단위입니다.

```jsx
const element = <h1>Hello, world</h1>;
```

![Untitled](Element%203c0f7973d4e548c08267ca8c7a205a07/Untitled.png)

- **Elements는 화면에서 보이는 것들을 기술한다**
- **리액트  Elements는 자바스크립트 객체 형태로 존재한다.**
- **리액트 엘리먼트는 immutable하다.**
- **Elements 생성후에는 children이나 attributes를 바꿀 수 없다.**
- **일반적으로 JavaScript의 React.createElement() 함수 또는 JSX의 태그 문법(ex. <Button />)으로 작성한다.**
- **엘리먼트들로 이뤄진 트리를 엘리먼트 트리라 부르며, 이는 메모리 상에만 존재하는 가상 DOM(Virtual DOM)이다.**