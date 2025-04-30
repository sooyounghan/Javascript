-----
### 일급 객체 (First Class Object)
-----
1. https://developer.mozilla.org/ko/docs/Glossary/First-class_Function
2. 함수를 변수와 같이 다루는 언어에 있는 개념
3. 자바스크립트의 함수도 일급 객체 (함수는 기본적으로 객체)
```js
function addNumbers(a, b) { return a + b; }

console.log(typeof addNumbers)
```
<div align="center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/d1c8da6a-fe86-47d7-a6b7-ab8acb97939a">
</div>

-----
### 일급 객체 (First Class Object) 특성
-----
1. 상수 또는 변수에 할당 가능
2. 다른 함수에 인자로 전달될 수 있음
3. 다른 함수의 결과값으로 반환될 수 있음

-----
### 할당
-----
```js
function isOddNum(number){
  console.log(
    (number % 2 ? '홀' : '짝')
    + '수입니다.'
  );

  return number % 2 ? true : false;
};

const checkIfOdd = isOddNum; // 뒤에 괄호 없음 주의

console.log(checkIfOdd(23));
```
  - checkIfOdd = isOddNum : 함수를 식별자로 하여 할당, 즉 함수를 할당
  - checkIfOdd = isOddNum() : 함수를 실행하여 그 함수의 return 값을 할당
<div align="center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/a5128936-e42b-4891-aac8-d02985774b4e">
</div>

```js
let x = 7, y = 3;

let func1 = (a, b) => a + b;
let func2 = (a, b) => a - b;

console.log(func1(x, y), func2(x, y));
```
<div align="center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/8fcb9356-2c93-400e-8c2a-66d75d90f139">
</div>

```js
func1 = func2;

console.log(func1(x, y), func2(x, y));
```
<div align="center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/90a65e05-2609-4284-b5e2-88101222307f">
</div>

  - func1은 func2를 가리키게 됨
    
1. 함수도 객체와 배열처럼 참조타입
2. 객체와 배열의 값으로도 할당 가능
```js
let person = {
  name : '홍길동',
  age : 30,
  married : true,
  introduce : function (formal) {
    return formal
    ? '안녕하십니까. 홍길동 대리라고 합니다.'
    : '안녕하세요, 홍길동이라고 해요.';
  }
};

console.log(person.introduce(true));
console.log(person.introduce(false));
```
  - function 뒤 함수명이 없음 : 즉, 함수명을 Propery인 introduce가 됨
<div align="center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/2bdefa38-c0d9-410b-b5ed-443c56614baf">
</div>

```js
let arithmetics = [
  (a, b) => a + b,
  (a, b) => a - b,
  (a, b) => a * b,
  (a, b) => a / b
];

for(arm of arithmetics) {
  console.log(arm(5, 3));
}
```
<div align="center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/8f433c56-0d0b-49d8-9333-1da7b0376bdb">
</div>

3. 객체의 함수 프로퍼티 : 메서드(Method)
4. ES6부터는 메서드의 정의가 달라짐 (단축 표현 메서드만 가리킴)
5. 객체에 함수 프로퍼티를 포함할 때 기억할 것
```js
let person = {
  name : '홍길동',
  age : 30,
  married : true,
  introduce : function () {
    return `저는 ${this.name}, ${this.age} 살이고 `
    + `${this.married ? '기혼' : '미혼'}입니다.`;
  }
};

console.log(person.introduce());
```
<div align="center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/35345f3e-6390-494c-9d97-79d975b000e2">
</div>

```js
let person = {
  name : '홍길동',
  age : 30,
  married : true,
  introduce : function () {
    return this;
  }
};

console.log(person.introduce());
```
  - 한 객체의 다른 프로퍼티에 접근 : this 사용
  - 객체 리터럴의 프로퍼티로는 this를 사용

<div align="center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/11983079-1871-4c9d-afd6-b212e3db82ff">
</div>

```js
let person = {
  name : '홍길동',
  age : 30,
  married : true,
  introduce : () => {
    return `저는 ${this.name}, ${this.age} 살이고 `
    + `${this.married ? '기혼' : '미혼'}입니다.`;
  }
};

console.log(person.introduce());
```
  - 화살표 함수에서는 접근 불가 (undefined로 인식되어 false)
<div align="center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/c6eaed7e-c10f-4dd2-85a4-01f03dbc89f8">
</div>

-----
### 인자로 전달
-----   
1. 함수가 다른 함수를 인자로 전달받음
2. 전달받는 함수 : 고차 함수(Highter-order Function)
3. 전달되는 함수 : 콜백 함수(Callback Function)
```js
let list = [1, 2, 3, 4, 5];

function doInArray(array, func) {
  for(item of array) {
    func(item);
  }
}

doInArray(list, console.log);
```
<div align="center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/0ac2c23f-c249-44c0-acff-7626476a0691">
</div>

  - console.log : console이란 객체에서 log란 키에 할당된 함수
  - doInArray : 고차 함수
  - console.log : 콜백 함수

4. 익명 함수(Anonymous Function)
```js
function doNTimes (func, repeat, x, y) {
  let result = x;
  for(let i = 0; i < repeat; i++) {
    result = func(result, y)
  }
  return result;
}

console.log(
  doNTimes((x, y) => x * y, 3, 5, 2),
  doNTimes((x, y) => x / y, 3, 5, 2)
);
```
<div align="center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/14bc0c0a-3058-4e6e-8006-c34f53a5cf64">
</div>

  - 익명 함수(Anonymous Function) : 인자로 전달된 함수들은 변수나 상수에 할당되지 않아 이름이 없음
  - 즉, (x, y) => x * y나 (x, y) => x / y는 익명함수 (doNTimes 내에서 func이라는 이름으로 붙여지는 것 처럼 사용)

5. 두 개의 Callback Function을 인자로 받음
```js
// Calculate
const add = (a, b) => a + b;
const subtract = (a, b) => a - b;
const multiply = (a, b) => a * b;

// Evaluate
const isOdd = (number) => !!(number % 2);
const isPositive = (number) => number > 0;

function calcAndEval (calc, eval, x, y) {
  return eval(calc(x, y));
}

console.log(
  calcAndEval(add, isOdd, 5, 7),
  calcAndEval(subtract, isPositive, 5, 7),
  calcAndEval(multiply, isOdd, 5, 7)
);
```
<div align="center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/1b86cc3c-49f5-468a-be45-2ecffdf3c553">
</div>

-----
### 결과값으로 반환 (함수를 다른 함수의 반환값으로 사용 가능)
-----   
```js
function getIntroFunc(name, formal) {
  return formal
  ? function() {
    console.log(`안녕하십니까, ${name}입니다.`);
  } : function() {
    console.log(`안녕하세요~ ${name}이라고 해요.`);
  }
}

const hongIntro = getIntroFunc('홍길동', true);
const jeonIntro = getIntroFunc('전우치', false);

hongIntro();
jeonIntro();
```
  - fucntion()은 어떤 반환 값에 변수명, 상수명이 있을 필요가 없으므로 익명 함수 형태
  - 즉, hongIntro는 어떤 Function 저장 (매개변수 없음)
  - 즉, jeonIntro는 어떤 Function 저장 (매개변수 없음)
<div align="center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/522a0918-a7e4-4a88-b1a5-3a6c1dddc6eb">
</div>

```js
const add = (a, b) => a + b;
const sub = (a, b) => a - b;
const mul = (a, b) => a * b;
const div = (a, b) => a / b;

function comb3ArmFuncs(armFunc1, armFunc2, armFunc3) {
  return (x, y) => armFunc3(armFunc2(armFunc1(x, y), y), y);
}

const add_mul_sub = comb3ArmFuncs(add, mul, sub);
const mul_add_div = comb3ArmFuncs(mul, add, div);
const div_add_mul = comb3ArmFuncs(div, add, mul);

console.log(
  add_mul_sub(10, 4),
  mul_add_div(10, 4),
  div_add_mul(10, 4)
);
```
  - 4개의 익명함수 선언 후 각 const 변수명에 할당
  - comb3ArmFuncs는 3개의 함수를 매개변수로 받아, 순서대로 실행하는데, 이렇게 실행하는 Function으로 반환 (역시 return문은 익명함수의 형태)
<div align="center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/5ffde939-0db5-46c7-a79a-c5a2d8970be2">
</div>

-----
### 커링 (Currying)
-----  
1. 필요한 인자보다 적은 수의 인자를 받으면, 나머지 인자를 인자로 받는 다른 함수를 반환
```js
// 기존 코드
function addMultSubt(a, b, c, d){
  return (a + b) * c - d;
}

const addMultSubt2 = (a, b, c, d) => (a + b) * c - d;

console.log(
  addMultSubt(2, 3, 4, 5),
  addMultSubt2(2, 3, 4, 5)
);
```
<div align="center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/39024849-65d3-4422-82fc-28501e8283c8">
</div>

2. 커링으로 작성된 함수
   - 충분한 수의 인자가 없다면, 일단 필요한 인자에 대해 처리, 나머지는 추후에 받아 처리
```js
function curryAddMultSubt(a) {
  return function(b) {
    return function(c) {
      return function(d) {
        return (a + b) * c - d;
      }
    }
  }
}

const curryAddMultSubt2 = a => b => c => d => (a + b) * c - d;

console.log(
  curryAddMultSubt(2)(3)(4)(5),
  curryAddMultSubt2(2)(3)(4)(5)
);
```
  - curryAddMultSubt는 a라는 인자를 받아 return function(b) { .. } 를 처리
  - function(b)는 b라는 인자를 받아 return function(c) { ... } 를 처리
  - function(c)는 c라는 인자를 받아 return function(d) { ... } 를 처리
  - function(d)는 d라는 인자를 받아(총 a, b, c, d) retrun (a + b) * c - d를 실행
  - a => b => c => d => (a + b) * c - d 설명
    + b는 a를 받음
    + c는 a, b를 받음
    + d는 a, b, c를 받아 (a + b) * c - d를 반환

  - 사용 방법은 curryAddMultSubt(2)(3)(4)(5), curryAddMultSubt2(2)(3)(4)(5)와 같이 사용


<div align="center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/2d50467d-8057-44a5-bdd0-9eaca337ce22">
</div>

```js
const curryAddMultSubtFrom2 = curryAddMultSubt(2);
const curryMultSubFrom5 = curryAddMultSubt(2)(3);
const currySubFrom20 = curryAddMultSubt(2)(3)(4);

console.log(curryAddMultSubtFrom2);
console.log(curryMultSubFrom5);
console.log(currySubFrom20);
```
  - curryAddMultSub2(2)는 2를 인자를 주어, 거기에 나머지 부분 처리하는 함수 할당
  - curryAddMultSubt(2)(3)는 2, 3을 인자를 주어, 해당 부분 함수까지 실행, 나머지 부분을 처리하는 함수 할당
  - curryAddMultSubt(2)(3)(4)는 2, 3, 4를 인자를 주어, 해당 부분 함수까지 실행, 나머지 부분을 처리하는 함수 할당
    
<div align="center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/b7cd0502-aded-423d-83a6-498e239efd22">
</div>

```js
const curryAddMultSubtFrom2 = curryAddMultSubt2(2);
const curryMultSubFrom5 = curryAddMultSubt2(2)(3);
const currySubFrom20 = curryAddMultSubt2(2)(3)(4);

console.log(curryAddMultSubtFrom2);
console.log(curryMultSubFrom5);
console.log(currySubFrom20);
```
  - 화살표 함수도 동일
<div align="center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/bc66a836-8a3c-475f-96e0-ea19df49dc80">
</div>

```js
console.log(
  curryAddMultSubtFrom2(3)(4)(5),
  curryMultSubFrom5(4)(5),
  currySubFrom20(5)
);
```
  - 위에서 인자로 받아야 할 값을 넣어주면 실행
<div align="center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/a4489862-0707-4190-a94a-5d2d4edf1dcb">
</div>

-----
### 참고사항
-----  
1. 하나의 함수는 한 가지 일만 하도록 설정
2. 하나의 함수가 여러 일을 수행하면, 이후 코드 수정하기 복잡해짐
3. 각자 하나의 일을 하는 여러 함수들의 조합으로 사용할 것
