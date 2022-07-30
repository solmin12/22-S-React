### React

자바스크립트 UI라이브러리

### React 장단점

장점

- 빠른 업데이트와 렌더링 속도 - Virtual DOM 사용
- Component-Based(웹사이트를 컴포넌트들의 조합으로 만듬)
- 재사용성

단점

- 방대한 학습량
- 높은 상태관리 복잡도

### JSX

자바스크립트의 문법을 확장

JavaScript + XML/HTML

내부적으로 작성된 XML/HTML코드가 자바스크립트 코드로 변환된다. → React.createElement가 수행

JSX 장점

- 코드가 간결해진다.
- 가독성 향상
- Injection Attacks 방어 - 보안성 향상

### SPA vs MPA

SPA(Single Page Application)

- 한개의 페이지로 구성된 Application이다.
- 웹 애플리케이션에 필요한 정적 리소스를 최초에 한번 다운로드 후 새로운 페이지 요청에 따라 필요한 데이터만 전달 받아 페이지를 갱신한다.

MPA(Multiple Page Application)

- 여러 개의 페이지로 구성된 Application이다.
- 새로운 페이지를 요청할 때마다 정적 리소스를 다운로드하고 매번 전체 페이지가 다시 렌더링 된다.

### React Element

- 리액트 앱을 구성하는 가장 작은 블록들
- 화면에서 보이는 것들을 작성
- 자바스크립트 객체 형태로 존재

모든 React 컴포넌트는 `React.createElement`에 의해 React Element로 변환된다. 

```jsx
function Button(props){
	return(
			<button className={`bg-${props.color}`}>
					<b>
							{props.children}
					<b>
			</button>
		)
}

function ConfirmDoalog(props){
	return(
			<div>
				<p>내용을 확인하셨으면 확인 버튼을 눌러주세요.<p>
				<Button color=`green`>확인</Button>
			<div>
		)
}

// 랜더링 후
{
  type: 'div',
  props: {
    children : [
      {
        type: 'p',
        props: {
          children : '내용을 확인하셨으면 확인 버튼을 눌러주세요.'
        }
      },
      {
        type: 'button',
        props: {
          className: 'bg-green',
          children: {
            type: 'b',
            props:{
              childre: '확인'
            }
          }
        }
      }
    ]
  }
}
```

### React Element 특징

- immutable(불변성): 한번 Element를 생성 후에는 children이나 attributes를 바꿀 수 없다!
- 새로운 화면 갱신은 기존 Element에서 새로운 변경 사항을 적용해 생성한 Element로 변경
    
    → 불변성 때문
    

### React Components

리액트의 페이지는 컴포넌트들의 조합으로 이루어져 있고, 각각의 컴포넌트들은 또 다른 컴포넌트들의 조합이다.

리액트 컴포넌트의 역할은 입력(props)을 받아 그에 맞는 출력(React Element)을 한다.

### Props

React Component의 속성을 말한다.

React Component에 전달할 정보를 담고있는 자바스크립트 객체이다.

### Props 특징

- Read-Only: 값을 변경할 수 없다. 값을 변경하기 위해서는 새로운 값을 컴포넌트에 전달해 새로운 Element를 생성한다.
- 모든 React Component는 Props를 직접 바꿀 수 없고, 같은 Props에 대해서는 항상 같은 결과를 보여야 한다.

### Function Component

props를 받아 React Element를 return하는 함수 형태의 컴포넌트

간결한 코드가 장점

### Class Component

React.Component를 상속받아 사용 → React.Component를 상속받았기 때문에 결과적으로 Class Component 또한 React Component이다.

Component의 이름은 항상 대문자로 시작해야 한다.

→ 소문자로 시작 시, React는 컴포넌트가 아니라 DOM태그로 인식

### Component 합성

Component를 여러 개 합쳐 Component를 만드는 것

### Component 추출

큰 컴포넌트에서 일부를 추출해 새로운 컴포넌트를 만드는 것

→ 재사용성과, 개발속도 상승

### State

React Component의 변경 가능한 데이터로 개발자가 정의해서 사용한다.

JavaScript 객체

정의된 state는 직접 수정하면 안된다.

### LifeSycle

Component는 계속 존재하는 것이 아니라 시간의 흐름에 따라 생성되고 업데이트 되다가 사라진다.