# 3주차

# [React] Rendering Elements

엘리먼트는 React 앱의 가장 작은 단위로, 화면에 표시할 내용을 기술한다. (엘리먼트가 모여서 컴포넌트가 된다.)

const element = <h1>Hello, world</h1>

리액트 엘리먼트는 immutable 하다. 엘리먼트를 생성한 이후에는 자식이나 속성을 변경할 수 없다.

UI를 업데이트하는 유일한 방법은 새 엘리먼트를 생성하고 ReactDOM.render()에 넘겨주는 것이다.

function tick() {
  const element = (
    <div>
      <h1>Hello, world!</h1>
      <h2>It is {new Date().toLocaleTimeString()}.</h2>
    </div>
  );
  ReactDOM.render(element, document.getElementById('root'));
}

setInterval(tick, 1000);

**Virtual DOM**

****

웹 브라우저는 DOM을 활용하여 객체에 자바스크립트와 CSS를 적용한다. 하지만 DOM은 동적 UI에 최적화되어 있지 않다. DOM에 변화가 일어나면 웹 브라우저는 CSS를 다시 연산하고, 레이아웃을 구성하고, 페이지를 리페인트한다. 이 과정에서 시간이 허비되고, 업데이트가 너무 잦으면 성능이 저하될 수 있다.

리액트는 Virtual DOM을 사용하여 실제 DOM 전체를 조작하는 대신 바뀐 부분만 최소한으로 조작한다.

리액트에서 웹 브라우저에 실제 DOM을 업데이트할 때는 다음 세 가지 절차를 밟는다.

1. 데이터를 업데이트하면 전체 UI를 Virtual DOM에 리렌더링한다.

2. 이전 Virtual DOM에 있던 내용과 현재 내용을 비교한다.

3. 바뀐 부분만 실제 DOM에 적용한다.