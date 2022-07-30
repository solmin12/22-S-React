postfix와 prefix의 결과값이다

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/92cc2709-7fe2-4337-b1df-cba9237ab672/Untitled.png)

이진 논리 연산자이다

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/2225f264-6a84-4a61-a399-f5c739f6c4a0/Untitled.png)

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/7706a056-3a67-4776-ae1b-40b5dd3b62b7/Untitled.png)

삼항 연산자이다

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/4a927feb-aeb9-44b1-b9b0-7f5a82a79c68/Untitled.png)

node.js는 js의 환경

DOM = 문서 객체 모델

virtual DOM 가상 DOM

업데이트 해야할 최소한의 부분만 변경하여 render에 도움을 줌

React는 component를 모아서 개발하는 것

재사용성을 가진다

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/2c8b84bc-722a-4e60-8c00-40dc41ab1a74/Untitled.png)

div root가 Root DOM Node (최상위 노드) 이다

npm start : 앱을 실행시킨다 (react app경로 위에서 시작해야 함)

localhost:3000으로 실행시킨다

localhost는 현재 내가 사용하고 있는 컴퓨터

JSX

js의 확장 문법

js 와 xml/html을 합친 것

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/b9a50f93-a2b1-47ca-8ca0-bbf8dfd421e9/Untitled.png)

xml/html 코드를 js로 바꿔준다

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/f277aa6f-fc3b-4861-8a52-dc1b1f022602/Untitled.png)

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/520fe726-a6f8-4b7d-b1da-f94cef1caad5/Untitled.png)

첫번 째는 type (h1같은) 또는 또다른 react component가 들어감

두번째는 props(속성 (class나 style등))

마지막이 해당 element의 자식 element가 들어감

라는 파라미터를 사용함

jsx 장점

코드가 간결해짐

유지보수가 좋고

버그를 찾기 좋고

injection attacks를 방지

데이터가 변환되서 들어가기에 (ex props값에 맞는 데이터를 가져와 실행시킴)

xss를 방어할 수 있음

jsx 사용법

html 코드를 쓰다가 js코드를 쓰고 싶을 때 중괄호에 넣어서 쓰면 됨

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/a0a57ee2-c93f-4ab0-82bf-9a6c280ccd3c/Untitled.png)

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/b0adac3a-b630-4aae-9922-80c62e51fad6/Untitled.png)

Book component는 props로 name과 numOfPage를 받아서 이를 출력하는 component이다

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/a11ba71e-adfe-4744-90f1-65bed05f3cae/Untitled.png)

Library Component도 만들었다

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/8606b4dc-ae40-483d-b734-bafd0eae8d40/Untitled.png)

index.js에서 Library component를 import 해오고

render에 Library를 가져옴으로써 출력할 수 있다

element (React Elements)

요소

react를 구성하는 가장 작은 블록들

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/6e27019f-8a77-40b9-b080-e517d6aa5a47/Untitled.png)

React Elements는 Dom Elements (실제 콘솔에서 보이는 Elements)의 가상 Elements라고 할 수 있다

React Elements는 JS의 객체 형태로 존재

Elements는 Component의 유형과 속성 및 내부의 모든 자식에 대한 정보를 포함하고 있는 일반적인 JS 객체이다

이 객체는 마음대로 바꿀 수 없는 불변성을 가지고 있음

React Element = immutable

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/0c798b3e-35e5-4ac3-99eb-9601526b25d8/Untitled.png)

     수정이 안됨으로

새로운 element를 만들어 기존의 것과 바꿔 쓰면 된다

Virtual DOM이기에 바꿔도 좋다

Elements Rendering하기

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/d4a5a7d6-3b26-4c9e-a3ca-b1fd698bf41c/Untitled.png)

Virtual DOM 에서 실제 DOM으로 되는 모습

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/fe067384-956d-47c5-b93a-7af8d88e4bb7/Untitled.png)

이것도 tick이 나올때마다 새로운 element를 생성해 바꾸는 것이다

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/0646a82f-4889-44d2-b5b9-083781b59cbb/Untitled.png)

clock 만들기 실습이다

new Date( )는 날짜와 시간을 얻기 위한 객체이다

toLocaleTimeString 메서드는 Date객체에서 날짜를 현재 지역 표기법으로 변환하여 가져온다

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/7b1e1061-dd0c-4d41-8a1a-d9747c53f7e5/Untitled.png)

마찬가지로 import해오고 setInterval을 이용해 1초마다 새로고침되게 만든다

리엑트 : Component-based

컴포넌트들이 모여 페이지를 이룸

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/45a378c1-a42f-423f-9fd5-5a66f7dd8a28/Untitled.png)

JS 함수와 React component는 입력과 출력이 있는 비슷한 형태라고도 볼 수 있다

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/423367e0-3b59-4840-a02b-33ced616356e/Untitled.png)

props를 넣어 component를 구성해 그 component로 element들을 만든다

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/bc5d078a-d1ad-42e2-bf87-e1c86ee12ebc/Untitled.png)

props가 재료고 재료에 따라 Element가 달라진다

props : readonly

바꿀 수 없음

마찬가지로 새로운 컴포넌트를 만들면 됨

pure함수와 impure함수

pure함수

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/12c80adf-8358-44b6-a3ac-4b09feb94d5d/Untitled.png)

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/71d48e29-3b1d-4dca-8a82-a325211be587/Untitled.png)

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/e01f3f52-49be-45a9-b860-6135c952cf4f/Untitled.png)

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/ef3ad622-ff1c-47bc-859a-4b9aa0ca366a/Untitled.png)

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/0289d14d-344b-4f1a-a9a9-59a1a6368c01/Untitled.png)

App component가 나오고 그 안에 Profile 컴포넌트가 있다

Profile안에는 3개의 속성들이 있다

중괄호를 사용한 것은 JS고 따움표는 데이터다 / 중괄호로 넣어도 된다

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/a58797c3-d627-4234-b6af-a73f1ef06d44/Untitled.png)

Layout이라는 컴포넌트에 width height는 정수값이고

header과 footer는 react element를 가지고 있다

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/064b7f0d-388b-4b03-a06f-bc9b672a591a/Untitled.png)

JS로 만들면 이렇게 되겠지만 JSX 쓰는 것을 추천한다

children이 없기에 null을 썼고

중괄호 안에는 props

처음 Profile은 React component이다

Component 만들기

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/474534b7-f5ce-45bf-a9dd-1e4e38123c82/Untitled.png)

Class Component를 개선해서 만든  Function component(Hook 사용)

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/87c91e25-34eb-49b8-a3ca-d234a59ee182/Untitled.png)

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/4b92fff2-472b-41bf-a96e-9ef2139f458f/Untitled.png)

React.Component라는 class를 상속받아서 Welcome이라는 class를 만듦

Component는 대문자로

Component 합성

Component안에 또 다른 Component를 쓸 수 있음

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/299830b3-5db9-469a-9242-fc987c7a6943/Untitled.png)

Welcome이라는 컴포넌트를 여러 번 씀

여러 개 컴포넌트를 합쳐서 또다른 컴포넌트를 만드는 것을 컴포넌트 합성이라고 함

Component 추출

재사용 가능한 component가 많아질수록 개발속도가 빨라짐

jsx에서 style 적용법

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/75d0610c-0071-444e-9cdf-db4ace328b7c/Untitled.png)

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/449f62ac-facd-44ba-a84f-460b962e429a/Untitled.png)

div 옆에 style = 만든 style과 이름을 적용

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/3e901883-03b4-4950-a59a-e4b86e081fa3/Untitled.png)

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/7cdc9835-20f7-4f2f-81b9-52927be1df91/Untitled.png)

props적용