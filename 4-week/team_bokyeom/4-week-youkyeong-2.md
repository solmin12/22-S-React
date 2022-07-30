# useMemo, useCallback

- 예시 코드 참고 사이트 : [https://react.vlpt.us/basic/17-useMemo.html](https://react.vlpt.us/basic/17-useMemo.html)
- useMemo, useCallback → 성능 최적화를 위해 사용 되는 hook으로, 의존성 배열 중 변경된 값이 존재하는 경우, memoized된 값을 반환한다는 특징을 갖음

---

## useMemo : 특정 결과 값의 재사용

### useMemo hook 사용 이전 (문제)
→ input창에 주는 입력은 user에게 아무런 변화를 주지 않음에도 불구하고 rendering 발생하는 문제발생

### useMemo hook 사용 (수정)

```jsx
...
function countActiveUsers(users) {
  console.log('활성 사용자 수를 세는중...');
  return users.filter(user => user.active).length;
}
...
//기존 코드
const count = countActiveUsers(users);
//useMemo적용 코드
const count = useMemo(() => countActiveUsers(users), [users]);
...
```

<aside>
💡 의존성 변수 <(users)>
의존성 배열 <[users]>로 설정된 값과 
동일하지 않은 경우에만 countActiveUsers함수 호출

→ 입력창에 발생한 event는 users배열에 영향을 미치지 않음 : 호출 X

</aside>

### useMemo hook 사용이후 (문제 해결)
→ 관련없는 변화에 대해서 불필요한 rerendering을 발생시키지 않음

## useCallback : 특정 함수의 재사용

### useCallback hook 사용 방법

```jsx
//기존 코드
...
const onCreate = () => {
    const user = {
      id: nextId.current,
      username,
      email
    };
    setUsers(users.concat(user));
    setInputs({
      username: '',
      email: ''
    });
    nextId.current += 1;
  };
  const onRemove = id => {
    setUsers(users.filter(user => user.id !== id));
  };
  const onToggle = id => {
    setUsers(
      users.map(user =>
        user.id === id ? { ...user, active: !user.active } : user
      )
    );
  };
...
//useCallback 적용 코드
...
const onCreate = useCallback(() => {
    const user = {
      id: nextId.current,
      username,
      email
    };
    setUsers(users.concat(user));
    setInputs({
      username: '',
      email: ''
    });
    nextId.current += 1;
  }, [users, username, email]);
  const onRemove = useCallback(
    id => {
      setUsers(users.filter(user => user.id !== id));
    },
    [users]
  );
  const onToggle = useCallback(
    id => {
      setUsers(
        users.map(user =>
          user.id === id ? { ...user, active: !user.active } : user
        )
      );
    },
    [users]
  );
...
```

<aside>
💡 함수 안에서 사용하는 상태나 props(함수 포함)가 존재한다면, deps 배열안에 꼭! 포함시킬 것 →반대의 경우, 최신값의 참조를 보장하지 않음

- 컴포넌트가 리렌더링될 때 함수가 새로 생성되는 것을 방지하며, 필요할 때 한번 생성한 것을 재사용

</aside>

### useCallback hook 성능의 변화

: 컴포넌트의 랜더링마다 함수의 재선언은 실제로 자바스크립트의 브라우저 실행속도를 고려하였을때 큰 의미 X, 의미있는 성능향상을 기대할 수 있는 경우

1. 의존 배열로 함수를 전달하는 경우 
**예시 상황** : useEffect가 function()을 참조하고 function()은 서버에서 값을 fetch할 때, function은 함수이기때문에 컴포넌트가 랜더링될때마다 새로 생성 
**문제** : useEffect()와 function()의 무한 랜더링 발생
**해결** : useCallback() 이용 시, 재 랜더링이 발생하더라도  function()이 서버에서 fetch한 값이 변하지 않는다면 동일한 함수의 참조값을 유지하므로 불필요한 재호출 방지
2. React.memo와 함께 사용
    
    <aside>
    💡 React.memo()를 사용해서 component를 감싸면 props값이 변경되지 않는 경우에 재호출을 방지
    
    </aside>
    
    **예시 상황** : 부모 Component가 자식 Component를 여러개 갖는 경우 불필요한 component의  rerendering을 방지하고자 React.memo를 사용하였지만, 부모 Component가 랜더링 될때 마다 참조값의 변화로 새로 랜더링
    
    **해결** : 자식 Component의 함수를 useCallback()으로 감싸고, 두 번째 인자로 함수가 의존하는 상태를 배열로 전달
    

### useCallback hook 주의사항

- 코드가 복잡성 및 유지보수의 어려움이 증기하기 때문에, 성능상 큰 의미가 없다면 사용하지 않는 것이 더 좋다.