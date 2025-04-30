-----
### 중첩된 함수
-----
1. 함수 안에서 선언된 다른 함수를 사용하여 그 함수 내에서 사용 가능 
```js
function outer() {
  const name = '바깥쪽';
  console.log(name, '함수');

  function inner() {
    const name = '안쪽';
    console.log(name, '함수');
  }
  inner();
}
outer();
```
<div align="center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/8a074daa-ce79-464a-8052-14e72a3c3c68">
</div>

  - outer 함수 안에 선언된 inner 함수는 outer 함수 내에서 사용
  - outer()를 실행하면, outer() 함수가 실행된 후, 내부 inner() 함수 실행

<div align="center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/4aa17d73-83d6-45c4-bae9-c6ae00d74923">
</div>
  - outer()의 Scope와 inner()의 Scope가 달라서 const name이 각각 사용된 걸 확인 가능

```js
function addMulSub(x, y) {
  const add = (a, b) => a + b;
  const sub = (a, b) => a - b;
  const mul = (a, b) => a * b;

  return sub(mul(add(x, y), y), y);
}

console.log(addMulSub(8, 3));
```
  - 함수 안에 또 다른 함수를 하나 이상 선언하여 사용 가능
<div align="center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/4916cf2d-54ea-47bc-956d-837c2178821e">
</div>

-----
### 재귀 함수 (Recursive Function)
-----
1. 자기 자신을 호출하는 함수
2. 중단 조건이 항상 필요

```js
function upto5(x) {
  console.log(x);
  if(x < 5) {
    upto5(x + 1);
  } else {
    console.log('- - -');
  };
}

upto5(1);
upto5(3);
upto5(7);
```
<div align="centeR">
<img src="https://github.com/sooyounghan/Web/assets/34672301/7360f8b6-e54a-4899-809d-27ce88909cdc">
<img src="https://github.com/sooyounghan/Web/assets/34672301/0a81109d-1d31-4016-a16d-1735ac72ff20">
</div>

  - 함수들은 한 함수가 다른 함수를 호출할 때 마다 컴퓨터 메모리 공간에 Call Stack 공간에 해당 함수에 대한 Stack이 쌓임
  - 즉, 재귀함수는 모든 재귀가 끝날때까지 계속 Call Stack 메모리상 공간 차지
  - Stack이 넘치면, Stack Overflow 발생
    + for문은 Loop를 돌면서 그 루프 하나 하나를 개별적 스택에서 진행

          * 일부 다른 언어에서는 꼬리 재귀(Tail Recursion)이라는 특정 방식으로 작성된 재귀함수는 Call Stack에 쌓이지 않도록 for문으로 변경해주기도 함
          * 자바스크립트는 해당 기능 대부분 미구현
      
< 팩토리얼 (Factorial) >
```js
function factorial(x) {
  return x === 0 ? 1 : x * factorial(x - 1);
}

console.log(
  factorial(1),
  factorial(2),
  factorial(3),
  factorial(4)
);
```
<div align="center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/0b425472-668d-44fd-a75a-24dbc7cdfc3b">
<img src="https://github.com/sooyounghan/Web/assets/34672301/72203bd8-8012-4728-b960-bd5ef50fbd5d">
</div>

-----
### 즉시 실행 함수 (Immideately Invoked Function Expression, IIFE)
-----
1. 오늘날에는 잘 사용되지 않음 (과거 코드 분석을 위해 사용)
```js
(function () {
  console.log('IIFE');
})();
```
  - 함수를 익명 함수로 선언한 후, 바로 실행 (함수명())
  - 즉, 함수나 배열에 넣지 않고, 바로 실행
<div align="center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/2b95ca46-40e0-4d25-97f3-6042655d0004">
</div>

2. 무엇에 사용되었는가?
< var 사용 >
```js
const initialMessage = (function () {
  // var 사용함에 주의
  var month = 8;
  var day = 15;
  var temps = [28, 27, 27, 30, 32, 30, 28];
  var avgTemp = 0;
  for(const temp of temps) {
    avgTemp += temp;
  }
  avgTemp /= temps.length;

  return `${month}월 ${day}일 평균 기온은 섭씨 ${avgTemp}도 입니다.`;
})();

console.log(initialMessage);
console.log(month); // 새로고침 후 const를 var로 바꾸고 실행해볼 것
```
<div align="center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/f12a0229-f3a0-419d-b919-6b6ff499d511">
</div>

  - 딱 한 번만 사용될 함수에 사용
  - 전역 변수들을 사용하지 않고, 복잡한 기능을 일회성으로 실행할 때 사용하여 메모리를 차지하는 것을 방지
  - 이전의 var는 블록 외에서 사용될 수 있었음 (단, IIFE로 설정하면, 해당 함수 외에서는 사용 불가)
  - 다른 코드들과의 변수명이나 상수명 충돌을 막기 위해 사용 (특히, 많은 코드 들이 사용될 때)
  - 오늘날에는 블록과 이후 배울 모듈의 사용으로 대체

  - month를 외부에서 사용하면 오류가 나도록 함수 안에 선언한 것
  - 이후 외부에서 선언할지 모를 다른 month와 이름이 겹치지 않도록 하기 위함

< const와 let 사용 >
```js
let initialMessage;

{
  const month = 8;
  const day = 15;
  const temps = [28, 27, 27, 30, 32, 32, 30, 28];
  let avgTemp = 0;
  for (const temp of temps) {
    avgTemp += temp
  }
  avgTemp /= temps.length;

  initialMessage = `${month}월 ${day}일 평균기온은 섭씨 ${avgTemp}도입니다.`;
};

console.log(initialMessage);
console.log(month); // 새로고침 후 const를 var로 바꾸고 실행해볼 것
```
<div align="center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/368a0bf2-dcf2-43d7-b908-5a175df55739">
</div>

< mont를 var로 사용하게 되면 ? >
```js
let initialMessage;

{
  var month = 8;
  const day = 15;
  const temps = [28, 27, 27, 30, 32, 32, 30, 28];
  let avgTemp = 0;
  for (const temp of temps) {
    avgTemp += temp
  }
  avgTemp /= temps.length;

  initialMessage = `${month}월 ${day}일 평균기온은 섭씨 ${avgTemp}도입니다.`;
};

console.log(initialMessage);
console.log(month);
```
<div align="center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/71e3faa3-78dc-4d75-84d7-fce2d0bd6622">
</div>

  - var는 블록 외에도 사용될 수 있으므로, 블록문 외에서도 month 값 출력 (이 문제를 위해서 IIFE를 사용)
  - 즉, 변수명이나 상수명의 충돌을 막기 위해 한 번만 사용될 함수의 변수들을 격리하고자 하는 목적으로 즉석 실행 함수를 사용한 것

-----
### 불변성 (Immutability)
-----
```js
let x = 1;
let y = {
  name : '홍길동',
  age : 15
}

let z = [1, 2, 3];

function changeValue (a, b, c) {
  a++;
  b.name = '전우치';
  b.age++;
  c[0]++;

  console.log(a, b, c);
}

changeValue(x, y, z);
```
<div align="center">
<img width="236" alt="20240405_095109" src="https://github.com/sooyounghan/Web/assets/34672301/df971866-1767-4fde-bbd9-13276c8933a8">
</div>
  - changeValue Function에 의해 x, y, z값이 변경된 상태로 출력

```js
console.log(x, y, z);
```
<div align="center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/1ec7eb51-6ff2-4e97-aab8-beba62ec1251">
</div>

  - x는 원시 타입, y와 z는 참조 타입
  - x는 실제 값이 복사되어 함수가 실행
  - y, z는 주소 값이 전달되어 함수가 실행

1. 원시 타입 : 인자로 들어간 함수 내에서의 변경에 영향을 받지 않음
   - 실제 값이 아니라 복사된 값이 들어갔기 때문임
2. 참조 타입 : 인자로 들어간 함수 내에서 요소가 변하면 실제로도 변함
   - 복사된 값도 같은 객체나 배열을 가리키기 때문

3. 함수에 주어진 인자를 변경하는 것은 좋지 않음
   - 외부의 환경을 변경하는 함수는 위험
   - 이상적인 함수 : 받은 값들만 처리하여 새로운 값을 반환
