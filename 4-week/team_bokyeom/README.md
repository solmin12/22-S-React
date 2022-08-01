# 4주차 RBF

---

[4주차 RandomBitFlip]

Mentor: @김보겸

Member: @김예훈 @모유경 @정유진 @장소윤 @박솔민

학습 범위: ReactComponent

Class Component

1. 생성자에서 state를 정의
2. setState()함수를 통해 state 업데이트
3. LifeCycle methods 제공

Function Component

별도로 state를 정의해 사용하거나 생명주기에 맞춰 코드가 실행되게 할 수 없음

이를 해결하기 위해 Hook을 사용

useState()

- state를 사용하기 위한 Hook
- 사용법

```
const [변수명, set함수명] = useState(초기값);
```

- class component에서는 setState()하나만 사용해서 모든 state의 변경이 가능했지만, function component에서는 각 변수마다 useState의 설정이 필요
- 비동기적 특성을 갖음 → componentDidUpdate(class component), useEffect(functional component)로 해결가능

useEffect()

- Side effect를 수행하기 위한 Hook
- Side effect란 다른 component에 영향을 미칠 수 있으며 렌더링 종료 이후에 실행될 수 있는 작업(effect)이 side로 실행된다는 의미
- 생명주기 함수와 동일한 기능을 수행할 수 있음
- component가 마운트/언마운트/업데이트 될 때 할 작업슬 선택하도록 하는 Hook 함수
- 사용법

```
useEffect(이펙트 함수, 의존성 배열);
//배열안에 있는 변수 중 하나라도 값이 변경되었을 때 이펙트 함수가 실행됨
useEffect(이펙트 함수);
//의존ㄴ성 배열 생략 가능 -> 컴포넌트가 업데이트 될때마다 호출
```

useMemo()

- Memoized value를 리턴하는 Hook
- Memoized value = Memoization된 결과값

<aside>
💡 Memoization
연산량이 많은 함수의 호출 결과를 저장해두었다가 같은 입력 값으로 함수를 호출할 경우 저장해두었던 호출 결과를 바로 반환하는 것

</aside>

- 사용법

```
const memoizedValue = useMemo(
	() => {
		//연산량이 높은 작업을 수행하여 결과를 반환
		return computeExpensiveValue(의존성 변수1, 의존성 변수2);
	},
	[의존성 변수1, 의존성 변수2]
);
```

useCallback()

- useMemo()와 유사하지만 값이 아닌 함수를 반환
- 의존성 배열이 바뀐 경우 함수를 새로 정의하여 리턴
- 사용법

```
const memoizedCallback = useCallback(
	() => {
//변수로서 받는 함수를 Callback이라 부름
		doSomething(의존성 변수1, 의존성 변수1);
	},
	[의존성 변수1, 의존성 변수2]
);
//의존성 변수가 바뀔 시 memoization된 Callback함수를 반환
```

useRef()

- Reference를 사용하기 위한 Hook
- Reference객체를 반환함
- 

<aside>
💡 Reference
특정 component에 접근할 수 있는 객체로 current속성이 존재
refObject.current = 현재 참조하고 있는 element

</aside>

- 사용법

```
const refContainer = useRef(초깃값);
//변수로 초깃값을 넣으면 해당 초깃값으로 초기화된 reference객체를 반환
//반환된 reference객체는 Component Mount해제 전까지 유지
```

- id, getElementById()를 사용하지 않고 ref를 사용하는 이유
- 예를들어 컴포넌트 안에 있는 DOM에 id를 지정한 후 해당 컴포넌트를 여러번 재사용하게 됐을 경우 유일해야 하는 id가 더 이상 유일하지 않고 그에 따른 문제가 생길 수 있다. 그래서 id값 대신 ref를 사용하는 것을 추천한다.

Self Closing

- 태그와 태그 사이에 아무 내용이 들어가지 않을 때, <태그 />로 표현 가능

리액트 Fragment

- 두 개 이상의 태그를 넣을 때, 꼭 하나의 태그로 닫아줘야 함
- div태그로 묶기 불편하면 <> </>로 묶어도 됨
- <> </>가 Fragment

리액트 주석

- {/* */}

Hook의 규칙

- Hook은 무조건 최상위 레벨에서만 호출해야 함 ex)반복문, 중첩문에서 Hook을 호출하면 안된다.
- Hook은 컴포넌트가 렌더링 될 때 마다 같은 순서로 호출되어야 함
- 리액트 함수 컴포넌트에서만 Hook을 호출해야 함

esling-plugin-react-hooks

- 위의 규칙을 강제하는 플러그인

Custom Hook

- 이름은 꼭 use로 시작해야 함
- 여러 개의 컴포넌트에서 하나의 Custom Hook을 사용할 때 컴포넌트 내부에 있는 모든 state와 effects는 분리되어 있음

Handling Events

- Event(사건)를 다루는 것을 Handling한다 함

```
//DOM의 Event
<button onclick="activate()">
  Activate
</button>

//React의 Event
<button onClick={activate}>
  Activate
</button>
```

DOM과 React의 Event 차이점

- Event이름의 표기법이 다름
- 함수를 전달하는 방식이 다름

<aside>
💡 camelCase
첫글자는 소문자, 중간에 나오는 새로운 단어의 첫글자는 대문자로 사용하여 글자의 크기가 변하는 모습이 마치 낙타의 등과 같다고 해서 지어진 이름

</aside>

Event Handler

- Event를 다루는 함수
- Event Listener라고 부르기도 함

Class Component에서 Event Handler추가하는 방법

1. bind(=binding) 사용
- 일반적으로 함수의 이름 뒤에, 괄호 없이 사용하는 경우에는 해당 함수 bind필수
- JS 기본적으로 class 함수들이 bound되지 않기때문에, 따로 bind를 하지 않으면 this.handleClick은 global 변수(undefind)에서 호출됨
- 객체 메서드를 Callback으로 전달할 때 ‘this 정보’가 사라지는 문제를 해결하기 위해 사용

<aside>
💡 this정보가 사라진다?
객체 메서드가 객체 내부가 아닌 다른 곳에 전달되어 호출되면 this가 사라짐

</aside>

- 모든 함수는 this를 수정하게 해주는 내장 메서드 bind를 제공

```
class Toggle extends React.Component{
  constructor(props){
     super(props);
     this.state={isToggleOn:true};

    //handleClick bind
     this.handleClick = this.handleClick.bind(this);
}

//handleClick정의 part
handleClick(){
   this.setState(prevState =>({
         isToggleOn:!prevState.isToggleOn
}));
}
render(){
   return(
       <button onClick={this.handleClick}>
              {this.state.isToggleOn ? '켜짐':'꺼짐'}
       </button>
     );
   }
}
```

[https://ko.javascript.info/bind](https://ko.javascript.info/bind)2. Class fields syntax 사용

```
class Toggle extends React.Component{

   //Class fields syntax
   handleClick = () => {
    console.log('this is : ' ,this);
  }
   //
  render(){
    return(
     <button onClick={this.handleClick}>클릭</button>
    );
  }
}
```

3. Arrow function(화살표 함수) 사용

- 해당 Compontnent(Toggle component)가 rendering될 때마다, 다른 callback함수가 생성되는 문제를 갖음 → 해당 component가 하위component의 prop으로 넘겨지게 되는 경우에는 하위 component에서 추가 rendering을 야기함

```
class Toggle extends React.Component{
    handleClick() {
    console.log('this is : ' ,this);
  }

  render(){
     return(
//Arrow function
     <button onClick={()=> this.handleClick()}>클릭</button>
//
    );
  }
}
```

Function Component에서 Event Handler추가하는 법

- Event를 넘겨줄 때 this를 사용하지 않고 정의한 eventHandler에 넘겨줌
- 함수 내부에 함수 정의, Arrow function으로 정의 2가지 방법

```
function Toggle (props){
  const [isToggleOn, setIsToggleOn]=useState(true);

   function handleClick(){//함수 내부에 함수로 정의하는 방법
      setIsToggleOn((isToggleOn)=>!isToggleOn);
   }
   const handleClick= () => {//Arrow function을 사용하여 정의하는 방법
      setIsToggleOn((isToggleOn)=>!isToggleOn);
   }

   return(
       <button onClick={handleClick}>//this.함수이름 NO, '함수이름'만
              {isToggleOn ? '켜짐':'꺼짐'}
       </button>
     );
   }
```

Arguments(인자)

- 함수에 전달할 데이터

Parameter

- 매개변수

Arguments와 Parameter의 차이점

```
function add(x,y){
  return x+y;
}
add(1,2);
//x,y는 매개변수
//1,2는 인자
```