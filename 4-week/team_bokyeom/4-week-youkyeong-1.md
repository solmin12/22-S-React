# Hook

## State

: rendering에 필요한 정보를 관리

### Class Component의 State

- 생성자에서 state 정의
- state update의 경우 setState() 사용
- Lifecycle methods 제공

### Function Component의 State

- state 사용 불가
- Lifecycle에 따른 기능 구현 불가

→class component의 기능을 동일하게 구현할 수 있는 **Hooks**

## useState

: state관련 hook

```jsx
//useState()사용법
const [변수명, set함수명] = useState(초기값);

//사용 예제
import React, {useState} from "react";

function Counter(props){
   const [count, setCount]= useState(0);
   return(
      <div>
         <p>{count}</p>
         <button onClick={()=> setCount(count+1)}></button>
      </div>
     );
}

```

- class component에서의 setState()호출-> state update -> component rerendering과 동일
- class component에서는 setState()하나만 사용해서 모든 state의 변경이 가능했지만, function component에서는 각 변수마다 useState의 설정이 필요
- useState(setState)는 비동기적 특성을 갖음 → componentDidUpdate(class component), useEffect(functional component)로 해결가능

<aside>
💡 효율적인 렌더링을 위해 여러개의 상태 값 변경 요청을 batch(일괄)처리

- 16ms단위로 batch update진행
- 변경된 상태값 merge해서, 이전과 변경된 지금의 element tree 비교작업(reconciliation)
- 변경된 부분만 DOM에 적용

</aside>

## useEffect

: side effect수행(lifecyle method의 수행)을 위한 hook

<aside>
💡 side effect 
: 다른 component에 영향을 미칠 수 있으며 렌더링 종료 이후에 실행될 수 있는 작업(effect)이 side로 실행된다는 의미

</aside>

- life cycle method인 componentDidMount, componentDidUpdate, componentWillUnmount와 동일한 기능을 한번에 통합하여 제공
- state의 변화를 감지하고 변할때 마다 rerendering

```jsx
//useEffect()사용법
useEffect(effect function, 의존성 배열);

//effect function이 mount, unmount시에 한 번씩만 실행
useEffect(effect function, []);

//component update마다 호출
useEffect(effect function);

//component unmount시 호출
useEffect(()=>{... return ()=>{effect function};});

//사용 예제
import React, {useState, useEffect} from "react";

function Counter(props){
   const [count, setCount]= useState(0);
   useEffect(()=>{
         document.title= 'Title is ${count}';
});
   return(
      <div>
         <p>{count}</p>
         <button onClick={()=> setCount(count+1)}></button>
      </div>
     );
}

```

## useRef

: reference를 사용하기 위한 Hook으로 referance객체를 반환함

<aside>
💡 reference
: 특정 컴포넌트에 접근할 수 있는 객체를 의미

reference객체에는 refObject.current(current속성)이 존재
: 현재 참조하고 있는 element

</aside>

- 반환된 reference객체는 component의 life time전체에 걸쳐 unmount 전까지 유지
- 변경가능한 current속성을 갖은 하나의 Container
- ref속성과 비교하여 useRef는 JS객체를 return하기때문에 다양한 변수를 저장할 수 있다는 차이를 갖음
- 랜더링 될 때 마다 같은 reference객체를 반환하기때문에 직접 current속성을 추가한 JS객체와의 차이를 갖음
- 내부 data변경시 rendering없이 바로 적용 → current속성 변경 시에도 재랜더링발생 x

<aside>
💡 DOM노드의 변화(연결/분리)로 event실행을 원하는 경우→ callback ref

 callback ref : ref가 다른 노드에 연결될때 마다 callback을 호출

</aside>

```jsx
//useRef()사용법
const refContainer = useRef(초깃값);
```

## useMemo

:Memoized value를 return하는 Hook

<aside>
💡 Memoization 
: 비용이 높은 함수의 호출결과를 저장하고, 같은 입력값에 대한 호출을 요구하는 경우 저장해둔 호출결과를 반환함

→  시간절약 및 중복 계산을 생략하여 최적화를 도움

</aside>

- useMemo Hook을 통해 전달된 함수는 rendering중에 실행됨 → side effect와 같이 rendering작업 동안에 실행되는 것을 지양하는 함수에 대해서는 x

```jsx
//useMemo()사용법
const memoizedValue = useMemo(
() => {
        return computeExpensiveValue(의존성 변수1, 의존성 변수2);
      },
      [의존성 변수1, 의존성 변수2]
);

//의존성 배열 생략 -> 매 renderiong마다 함수 실행, 의미없는 Hook사용
const memoizedValue = useMemo(
() =>  return computeExpensiveValue(의존성 변수1, 의존성 변수2);

//의존성 배열이 빈배열인 경우 -> component mount시에만 호출
const memoizedValue = useMemo(
() =>  return {
          computeExpensiveValue(의존성 변수1, 의존성 변수2);
          },[]);
```

## useCallback

: component의 rerendering마다 함수를 매번 새로 정의하는 것이 아닌, 의존성 배열의 값이 바뀌는 경우에만 함수를 새로 정의해서 return 

- 의존성 배열 중 변경된 값이 존재하는 경우, memoized된 값을 반환한다는 것이 useMemo hook과 유사하나 return값이 memoized callback 함수라는 차이를 갖는다.
- 의존성 배열이 빈배열인 경우에는  component mount시에만 호출