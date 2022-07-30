# Team 유빈

### Hooks

fuction component는 class component와는 다르게 state사용이 불가하고 Lifecycle에 따른 기능 구현이 불가능하다

→ Hooks로 해결(class component의 기능 사용 가능)

훅은 원하는 시점에 state, Lifecycle 관련 함수를 실행하게 한다. 

모두 use를 앞에 붙혀 사용

**대표적인 Hook**

- `useState()` : state를 사용하기 위한 Hook

    ```jsx
    const[변수명, set함수명] = useState(초기값);
    ```

- `userEffect()` :

    Side effect를 사용하기 위한 Hook

     생명주기 함수와 동일한 효과 

    ```jsx
    //의존성 배열의 값 중 하나라도 변경될 시 함수 실행
    useEffect(이펙트 함수, 의존성 배열);
    
    //mount, unmount 시에 한 번씩만 실행
    useEffect(이펙트 함수,[]);
    
    //Component가 업데이트 될 때마다 실행
    useEffec(이펙트 함수);
    
    useEffect(() => {
    	return () => {
    		// 컴포넌트 마운트가 해제되기 전 실행
    	}
    },)
    ```

- `userMemo()` :

    Component 랜더링 시 연산량이 높은 작업의 반복을 방지

    ```jsx
    const memoizedValue = useMemo(
    	() => {
    		//연산량이 높은 작업을 수행하여 결과를 반환
    		return computeExpensiveValue(의존성 변수1, 의존성 변수2);
    	},
    	[의존성 변수1, 의존성 변수2]
    );
    ```

    userMemo의 함수는 랜더링이 일어나는 중에 실행되기 때문에 랜더링 중 실행되면 안되는 작업을 작성하면 안된다.

- `userCallback` : userMemo와 거의 똑같지만 값이 아닌 함수를반환
- `useRef()` :

    특정 컴포넌트에 접근할 수 있는 객체(Reference)를 사용하기 위한 Hook 

    ```jsx
    const refContainer = userRef(초기값);
    ```


**Hook의 규칙**

Hook은 무조건 최상위 레벨에서만 호출해야 한다.

React fuction Component에서만 Hook을 호출해야 한다.

### Event

Class component에서 이벤트 함수를 사용하기 위해서는 bind를 해줘야 한다.

fuction component에서 이벤트 함수 정의

1. 함수 안에 함수로 정의
2. 화살표 함수를 사용하여 정의

### Conditional Rendering

어떠한 조건에 따라 렌더링이 달라지는 것

Element Variable은 React Component를 변수처럼 사용하는 방법

**Inline Condtions**

- &&
- 삼항 연산자

컴포넌트를 랜더링 하고 싶지 않을 때는 null을 return


## Quiz - D1

1. 다음 각각의 useEffect() 훅의 이펙트 함수가 언제 실행되는지 쓰시오.
```jsx
    //1. --
    useEffect(이펙트 함수, 의존성 배열);
    
    //2. -- 
    useEffect(이펙트 함수,[]);
    
    //3. --
    useEffec(이펙트 함수);
    
    useEffect(() => {
    	return () => {
    		//4. --
    	}
    },)
```
2. 각 문제가 어떻게 렌더링 되는지 쓰시오
```jsx
    const num = 5;
    // 1. --
    {num > 0 && 
      <h1>출력{num}</h1>
    }
    // 2. --
    <h1> {num > 7 ? '참' : '거짓'} </h1>
```

----------------------

### map() - List렌더링

```jsx
const numbers = [1,2,3,4,5];
const listItems = numbers.map((number) =>
	<li key={}>
			{number}
	</li>
);
```

**key값 지정**

1. 값으로 지정: `<li key={numbers.toString()}>` 

    → 배열 값이 중복이면 key값의 중복이 생길 수 있다.

2. id로 지정
3. index로 지정: id가 없을때만 사용, default

### Form

Controlled Component: 값이 React의 통제를 받는 Input Form Element

→ 여러개의 입력 양식의 값을 원하는데로 제어 가능!(입력 값이 Controlled Component의 state로 관리되기 때문)

**Form 종류**

```jsx
// input 태그
<input type="text" value={value} onChange={handleChange}/>
// textarea 태그
<textarea value={value} onChange={handleChange}/>
// select 태그
<select value={value} onChange={handelChange}>
	<option value="apple">사과</option>
	<option value="banana">바나나</option>
</select>
```

파일 input

`<input type=”file”>` :읽기 전용이기때문에 Uncontrolled Component

## Quiz - D2

1. 다음 코드의 문제점은?
```jsx
const numbers = [1,2,3,2,5];
const listItems = numbers.map((number) =>
	<li key={numbers.toString()}>
			{number}
	</li>
);
```

2. Mutiple Input을 제어하는 방법은?