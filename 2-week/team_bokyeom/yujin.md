# 2주차

### Call-back

함수를 매개변수로 던지고, 특정 조건이 발생하면 해당 함수를 호출.

기본형 call-back구현은 간단한 비동기 함수 호출에는 유리하나, 복잡한 작업에서는

잘못하면 콜백 지옥 발생

### Promise

Promise에 등록한 Call back으로 던진 함수가 완료되면, then/catch/finally 구문을 수행

다중 콜백이 필요했던 case를 간소화할 수 있음

### async & await

새로운 API는 아니고, promise api를 wrapping(syntactic sugar) 처리한 기능

비동기 처리할 함수를 async로 선언하고, Promise API 앞에 await를 추가. 

(await은 Promise & Promise를 return하는 함수 앞에 붙어야함)

**Callback**

****

자바스크립트의 함수는 객체이다.

1. 변수나 데이터안에 담길 수 있다.

2. 매개변수로 전달 할 수 있다.

3. 반환 값으로 사용할 수 있다.

4. 실행도중에 생성될 수 있다.

콜백함수는 이 중에서 2번째 특징을 활용한 것으로

간단하게 다른 함수에 매개변수로 넘겨준 함수를 말한다.

매개변수로 넘겨받은 함수는 일단 넘겨받고, 때가 되면 나중에 호출(Called back)하는 것이 콜백함수이다.

function checkGang(count, link, good) {
  count < 3 ? link() : good();
}

checkGang 함수에 count 라는 정수 변수와, link와 good라는 함수가 변수로 들어가 있다.

이후 count값에 따라 link나 good 함수가 나중에 호출(Called back) 되는 것이다.

콜백함수가 사용되는 이유는 무엇일까?

변수의 유호범위(scope)와 동기/비동기(Synchronous/Asynchronous) 처리에 대해 알아야 한다.

자바스크립트는 스레드가 하나인 프로그램이기 때문에

프로그램의 속도를 높이기 위해 비동기 처리를 하게 된다.

하지만 프로그램 중에는 다른 함수의 return 값을 받고 그 값에 따른 함수를 사용해야하는 동기 방식의 함수도 필요하다.

그렇기에 called back 함수를 사용하여 순서대로(동기적으로) 함수를 사용할 수 있게 한다.

//﻿JavaScript is synchronus.
//Execute the code block in order after hoisting
//hoisting: var, function declaration

console.log('1');
setTimeout( () => console.log('2'), 1000);
console.log('3');
//1 3 2

//Synchronous callback
function printImmediately(print) {
 print();
}
printImmediately(() => console.log('Immediately'));

//Asynchronous callback
function printWithDelay(print, timeout) {
 setTimeout(print, timeout);
}
printWithDelay(() => console.log('async callback'), 2000);

//1 3 Immediately 2 async callback

//Callback Hell example
class UserStorage {
 loginUser(id, password, onSucces, onError) {
  setTimeout( () => {
   if(
    (id === 'ellie' && password === 'dream') ||
    (id === 'coder' && password === 'academy')
   ) {
    onSucces(id);
   } else{
    onError(new Error('not found'));
   } 
  },2000);
 }

 getRoles(user, onSuccess, onError) {
  setTime(() => {
   if (user === 'ellie') {
    onSuccess({name: 'ellie', role: 'admin'});
   } else {
    onError(new Error('no acces'));
   } 
  }, 1000);
 }
}

let user = new UserStorage();
let id = propmt('enter your id');
let password = prompt('enter your id');

user.loginUser(
 id, 
 password, 
 (user) => {
  getRoles(
   user, 
   (userWithRole) => alert(`Hello ${userWithRole.name}, you have a ${userWithRole.role} role`);
   (err) => console.log(err)
  );
}, (err) => console.log(err));

**하지만!!**

이 콜백 함수 또한 단점이 있었으니,

콜백은 함수의 매개변수로 함수를 넣기 때문에 가독성이 매우 떨어진다.

거기에 콜백에 콜백에 콜백이 무는 로직을 짜야하는 복잡한 경우가 생기게 되었다.

이로인해 가독성 뿐만 아니라 오류 찾기도 힘들어지자 이를 보안하고 나온 것이 바로.

Promise 함수이다.

---

**Promise**

****

콜백함수와 달리 실행과 동시에 함수를 전달하지 않고

then()을 이용해서 콜백 함수를 첨부하는 방식으로 바뀌었다.

const checkGang = new Promise((resolve, reject) => {
  count < 3 ? resolve(line) : resolve(good);
}

checkGang
 .then((status) => {console.log(status)});

//Promise is a JS object for asynchronous operation.
// state: pending -> fulfilled or rejected
// Producer vs Consumer

//1. Producer
// when new Promise is created, the executor runs automatically!!!
const promise = new Promise( (resolve, reject) => {
 //this is executor
 //doing some heavy work (EX: network, read files...)
 console.log('doing something...');
 setTimeout( () => {
  //resolve('ellie');
  //reject(new Error('no network'));
 }, 2000);
}); 
//doing something...

// 2.Consumers: then, catch, finally
promise
 .then( value => {
  console.log(value); //ellie
 })
 .catch(error => {
  console.log(error); //no network
 })
 .finally( () => {
  console.log('finally'); //finally
 });
 
// 3.Promise chaining
const fetchNumber = new Promise((resolve, reject) => {
 setTimeout( () => resolve(1), 1000);
});

fetchNumber
 .then(num => num * 2) //2
 .then(num => num * 3) //6
 .then(num => {
  return new Promise((resolve, reject) => {
   setTimeout( () => resolve(num-1), 1000);
  });
 }) //5
 .then( num => console.log(num)); //5 (2 seconds)

// Error Handling
const getHen = () =>
 new Promise((resolve, reject) => {
  setTimeout(() => resolve('Hen'), 1000);
 });

const getEgg = hen =>
 new Promise((resolve, reject) => {
  //setTimeout(() => resolve(`${hen} => Egg`), 1000);
  //setTimeout(() => reject(new Error('no egg'), 1000);
 });

const cook = egg =>
 new Promise((resolve, reject) => {
  setTimeout(() => resolve(`${egg} => Cook`), 1000);
 });

getHen
 .then( hen => getEgg(hen)) //.then(getEgg)
 .then( egg => cook(egg)) //.then(cook)
 .then( meal => console.log(meal)); //.then(console.log);
//Hen => Egg => Cook

getHen
 .then( hen => getEgg(hen)) //.then(getEgg)
 .then( egg => cook(egg)) //.then(cook)
 .then( meal => console.log(meal)) //.then(console.log);
 .cath( error => console.log(error)); //.then(console.log);
//no egg

getHen
 .then( hen => getEgg(hen)) //.then(getEgg)
 .catch( error => return 'Man')
 .then( egg => cook(egg)) //.then(cook)
 .then( meal => console.log(meal)); //.then(console.log);
//Man => Cook

//Callback Hell example
class UserStorage {
 
 loginUser = (id, password) => return new Promise((resolve, reject) => {
  setTimeout( () => {
   if(
    (id === 'ellie' && password === 'dream') ||
    (id === 'coder' && password === 'academy')
   ) {
    resolve(id);
   } else{
    reject(new Error('not found'));
   } 
  },2000);  
 });

 getRoles = user => return new Promise((resolve, reject) => {
  setTime(() => {
   if (user === 'ellie') {
    resolve({name: 'ellie', role: 'admin'});
   } else {
    reject(new Error('no acces'));
   } 
  }, 1000);
 });
}

let user = new UserStorage();
let id = propmt('enter your id');
let password = prompt('enter your id');

user.loginUser(id, password)
 .then((user) => user.getRoles(user)) //.then(user.getRoles)
 .then( (userWithRole) => alert(`Hello ${userWithRole.name}, you have a ${userWithRole.role} role`))
 .catch(console.log);

---

**async, await**

//clear style of using promise

//1. async

//function
function fetchUser() {
 //do network request in 10 secs...
 return 'ellie';
}

const user = fetchUser();
console.log(user); //10secs later.. and ellie

//promise
function fetchUser() {
 return new Promise((resolve, reject) => {
  //do network request in 10 secs...
  resolve('ellie');
 });
}

const user = fetchUser();
console.log(user); //ellie

//async 
//async function == promise
async function fetchUser() {
 //do network request in 10 secs...
 return 'ellie';
}

const user = fetchUser();
console.log(user); //ellie

//2. await

//promise
function delay(ms) {
 return new Promise(resolve => setTimeout(resovle, ms));
}

function getApple() {
 return delay(3000)
 .then(() => "Apple")
}

function getBanana() {
 return delay(3000)
 .then(() => "Banana");
}

function pickFruits() {
 return getApple()
 .then((apple) => {
  return getBanana().then(banana => `${apple} + ${banana}`);
 });
}
 
pickFruits().then(console.lob); //Apple + Banana

//await
function delay(ms) {
 return new Promise(resolve => setTimeout(resovle, ms));
}

async function getApple() {
 await delay(3000);
 return "Apple";
}

async function getBanana() {
 await delay(3000);
 return "Banana";
}

async function pickFruits() {
 try{
  const apple = await getApple(); //3secs await 
  cosnt banana = await getBanana(); //apple 3초 기다린 후 다시 3초
  return `${apple} + ${banana}`; //6secs await....
 } catch(err){
  console.log(err);
 }
}
 
pickFruits(); //Apple + Banana

//병렬처리
async function pickFruits() {
 try{
  const applePromise = getApple(); //실행
  const bananaPromise = getBanana(); //실행
  const apple = await applePromise; //3secs await
  cosnt banana = await bananaPromise; //3secs await
  return `${apple} + ${banana}`; //3secs await....
 } catch(err){
  console.log(err);
 }
}

//3. useful Promise APIs (병렬처리 코드 더러워)
function pickAllFruits() {
 return Promise.all([getApple(), getBanana()]).then(fruits =>
  fruits.join('+')
 );
}
pickAllFruits().then(console.log); //Apple + Banana

function pickOnlyOne() {
 return Promise.race([getApple(), getBanana())]);
}
pickOnlyOne().then(console.log);//Apple

//Callback Hell example
class UserStorage {
 
 loginUser = (id, password) => return new Promise((resolve, reject) => {
  setTimeout( () => {
   if(
    (id === 'ellie' && password === 'dream') ||
    (id === 'coder' && password === 'academy')
   ) {
    resolve(id);
   } else{
    reject(new Error('not found'));
   } 
  },2000);  
 });

getRoles = user => return new Promise((resolve, reject) => {
  setTime(() => {
   if (user === 'ellie') {
    resolve({name: 'ellie', role: 'admin'});
   } else {
    reject(new Error('no acces'));
   } 
  }, 1000);
 });
}

let user = new UserStorage();
let id = propmt('enter your id');
let password = prompt('enter your id');

try{
 const users = await user.loginUser(id, password);
 const userWithRole = await user.getRoles(users);
 alert(`Hello ${userWithRole.name}, you have a ${userWithRole.role} role`);
} catch(err){
 console.log(err)
}

**[출처]** [10. Call back, Promise, async/await](https://blog.naver.com/leeminwok/222578775551)|**작성자** [IMNOOK](https://blog.naver.com/leeminwok)

# Blocking(블로킹) / Non-blocking(논블로킹)

블로킹과 논블로킹은 A 함수가 B 함수를 호출했을 때, **제어권을 어떻게 처리하느냐에 따라 달라진다.**

### 1) 블로킹

**블로킹**은 A 함수가 B 함수를 호출하면, **제어권을 A가 호출한 B 함수에 넘겨준다.**

![https://velog.velcdn.com/images%2Fnittre%2Fpost%2F8cdc0a02-d469-47d5-96c8-f6aeef204eb7%2Fimage.png](https://velog.velcdn.com/images%2Fnittre%2Fpost%2F8cdc0a02-d469-47d5-96c8-f6aeef204eb7%2Fimage.png)

1. A함수가 B함수를 호출하면 B에게 제어권을 넘긴다.
2. 제어권을 넘겨받은 B는 열심히 함수를 실행한다. A는 B에게 제어권을 넘겨주었기 때문에 함수 실행을 잠시 멈춘다.
3. B함수는 실행이 끝나면 자신을 호출한 A에게 제어권을 돌려준다.

### 2) 논블로킹

**논블로킹**은 A함수가 B함수를 호출해도 **제어권은 그대로 자신이 가지고 있는다**.

![https://velog.velcdn.com/images%2Fnittre%2Fpost%2Fc839fc04-1788-4063-ab38-b0d4a312dbf4%2Fimage.png](https://velog.velcdn.com/images%2Fnittre%2Fpost%2Fc839fc04-1788-4063-ab38-b0d4a312dbf4%2Fimage.png)

1. A함수가 B함수를 호출하면, B 함수는 실행되지만, **제어권은 A 함수가 그대로 가지고 있는다.**
2. A함수는 계속 제어권을 가지고 있기 때문에 B함수를 호출한 이후에도 자신의 코드를 계속 실행한다.

## 3. Synchronous(동기)와 Asynchronous(비동기)

동기와 비동기의 차이는 **호출되는 함수의 작업 완료 여부를 신경쓰는지의 여부**의 차이이다.

### 1) 동기

함수 A가 함수 B를 호출한 뒤, **함수 B의 리턴값을 계속 확인하면서 신경쓰는 것**이 동기이다.

### 2) 비동기

함수 A가 함수 B를 호출할 때 **콜백 함수를 함께 전달**해서, 함수 B의 작업이 완료되면 함께 보낸 콜백 함수를 실행한다.

함수 A는 함수 B를 호출한 후로 **함수 B의 작업 완료 여부에는 신경쓰지 않는다.**

## 4. 블로킹과 논블로킹, 동기와 비동기 비교

### 1) Sync-Blocking

동기를 블로킹처럼 실행하는 것은 이해하기 쉽다.

![https://velog.velcdn.com/images%2Fnittre%2Fpost%2Ff6212fee-ee42-4023-ae02-d2dc15eec46a%2Fimage.png](https://velog.velcdn.com/images%2Fnittre%2Fpost%2Ff6212fee-ee42-4023-ae02-d2dc15eec46a%2Fimage.png)

함수 A는 함수 B의 리턴값을 필요로 한다(**동기**). 그래서 제어권을 함수 B에게 넘겨주고, 함수 B가 실행을 완료하여 리턴값과 제어권을 돌려줄때까지 기다린다(**블로킹**).

### 2) Sync-Nonblocking

그런데, 동기를 논블로킹처럼 작동시킬 수 있다. 다음의 그림을 보자.

![https://velog.velcdn.com/images%2Fnittre%2Fpost%2Ffe5d1231-4c3c-4caf-bdd8-2287926e38ca%2Fimage.png](https://velog.velcdn.com/images%2Fnittre%2Fpost%2Ffe5d1231-4c3c-4caf-bdd8-2287926e38ca%2Fimage.png)

A 함수는 B 함수를 호출한다. 이 때 **A 함수는 B 함수에게 제어권을 주지 않고**, 자신의 코드를 계속 실행한다(**논블로킹**).

그런데 **A 함수는 B 함수의 리턴값이 필요하기 때문**에, 중간중간 B 함수에게 함수 실행을 완료했는지 물어본다(**동기**).

즉, 논블로킹인 동시에 동기인 것이다.

### 3) Async-Nonblocking

비동기 논블로킹은 이해하기 쉽다. A 함수는 B 함수를 호출한다.

이 때 제어권을 B 함수에 주지 않고, 자신이 계속 가지고 있는다(**논블로킹**). 따라서 B 함수를 호출한 이후에도 멈추지 않고 자신의 코드를 계속 실행한다.

그리고 B 함수를 호출할 때 **콜백함수**를 함께 준다. B 함수는 자신의 작업이 끝나면 A 함수가 준 콜백 함수를 실행한다(**비동기**).

![https://velog.velcdn.com/images%2Fnittre%2Fpost%2Fb9566928-9a6b-4111-9cad-528daa45475d%2Fimage.png](https://velog.velcdn.com/images%2Fnittre%2Fpost%2Fb9566928-9a6b-4111-9cad-528daa45475d%2Fimage.png)

### 4) Async-blocking

Async-blocking의 경우는 사실 잘 마주하기 쉽지 않다.

A 함수는 B 함수의 리턴값에 신경쓰지 않고, 콜백함수를 보낸다(**비동기**).

그런데, B 함수의 작업에 관심없음에도 불구하고, A 함수는 B 함수에게 제어권을 넘긴다(**블로킹**).

따라서, A 함수는 자신과 관련 없는 B 함수의 작업이 끝날 때까지 기다려야 한다.

![https://velog.velcdn.com/images%2Fnittre%2Fpost%2F9b6754f0-8721-4308-8a62-d884c7315d15%2Fimage.png](https://velog.velcdn.com/images%2Fnittre%2Fpost%2F9b6754f0-8721-4308-8a62-d884c7315d15%2Fimage.png)

Async-blocking의 경우 sync-blocking과 성능의 차이가 비슷하기 때문에 사용하는 경우는 거의 없다.

