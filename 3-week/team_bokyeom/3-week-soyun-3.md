# 토요일

![KakaoTalk_20220723_114529315.png](%E1%84%90%E1%85%A9%E1%84%8B%E1%85%AD%E1%84%8B%E1%85%B5%E1%86%AF%201bcc3455b5304345bf78cbeec6abc97b/KakaoTalk_20220723_114529315.png)

리액트는 컴포넌트 기반의 언어.
레고블록 조립하듯 컴포넌트들을 모아서 개발
컴포넌트들을 반복해서 사용.
작은 컴포넌트->하나의 컴포넌트들 모여서->웹페이지를 이룸
코드의양과 개발시간, 유지비수비용을 줄일 수 있음.

입력을 받아서 출력하므로, 리액트 컴포넌트를 자바스크립트의함수개념으로 생각해도 좋음.
컴포넌트와 엘리먼트의 관계는 클래스와 인스턴스 관계와 비슷하다.
입력: Props
출력: React element

리액트 컴포넌트는 Props를 받아 react element 를 생성하여 반환해줌

1. Props(Property: 속성)\
정의: 컴포넌트에 전달할 다양한 정보를 담고있는 자바스크립트 객체
무엇의 속성? 컴포넌트의 속성
특징;
- Read only. 값을 변경할 수 없다.
함수는 Pure하다? 입력값을 변경하지 않으며, 같은 입력값에 대해서는 항상 같은 출력값을 리턴
Impure한 함수: 함수기능이 입력값을 변경해주는거일때
모든 리액트 컴포넌트는 Props를 직접 바꿀 수 없고, 같은 Props에 대해서는 항상 같은 결과를 보여줄것.
- 문자열 이외의 것은 중괄호로 감싸주어야 한다. jsx의 코드
- 프로필 양식을 하나의 컴포넌트로 만들고, 각 학회원들의 정보를 Props로 하는 웹

1. 컴포넌트
class component 이게 불편해서
function component 이걸 만들면서 훅의 개념도 나왔다.

Class Component: (extends React.Component)
Function component :

컴포넌트의 이름은 항상 대문자로 시작해야한다.
소문자로 시작하는 건 돔 태그로 인식하기때문.

1. 컴포넌트 합성
여러개의 컴포넌트를 포함하여 새로운 컴포넌트를 만드는거.

1. 컴포넌트 추출

1. State
-리액트 component의 상태를 의미.
- 리액트 component의 변경 가능한 데이터라는 의미에 더 가까움.
-state는 개발자가 직접 정의한다.
-렌더링이나 데이터 흐름에 사용되는 값만 state에 포함시켜야함.(불필요한값이 포함되고, 그게 변경될 경우 렌더링이 불필요하게 일어나고, 성능저하를 시킬 수 있기 때문)
불필요한 값은 instance에 정의하면됨?
결론: state는 JavaScript의 객체이다.
클래스 컴포넌트는 컴포넌트의 state를 this.state라는 생성자로 정의.
setState라는 함수로 state를 변경해야함
함수형 컴포넌트는 컴포넌트의 state를 use 라는 훅으로 정의
1. 생명주기
2. 출생(Mounting)
생성자가 constructor로 컴포넌트를 생성한다.
생명주기 함수(라이프사이클메서드): componentDidMount
3. 인생(Updating)
props,state가 변경된다.(New props, setState(), forceUpdate()
생명주기 함수(라이프사이클메서드):componentDidUpdate
4. 사망(Unmounting)
언제? 상위 컴포넌트에서 현재 컴포넌트를 더이상 화면에 표시하지 않을 때.
생명주기 함수(라이프사이클메서드): componentWillUnmount
- -> component 는 계속 존재하는 것이 아니라 생성되고 사망하기도 한다.

시간이없어서 예쁘게 꾸미지는 못했습니다..
이번 주말에 예쁘게 꾸미겠습니다.