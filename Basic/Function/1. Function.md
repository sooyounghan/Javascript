-----
### Function
-----
: 함수 또한 객체임
```js
function 함수명 (입력값) {
  // 수행할 문장
  return 반환값;
}

함수명(입력값)
```

1. 함수를 사용한다는 것 : 반복될 수 있는 작업을 정의해두는 것
```js
// 함수 사용 전
let a = 3, b = 4;

console.log(`${a} + ${b} = ${a + b}`);
console.log(`${a} - ${b} = ${a - b}`);
console.log(`${a} * ${b} = ${a * b}`);
console.log(`${a} / ${b} = ${a / b}`);

let c = 10, d = 2;

console.log(`${c} + ${d} = ${c + d}`);
console.log(`${c} - ${d} = ${c - d}`);
console.log(`${c} * ${d} = ${c * d}`);
console.log(`${c} / ${d} = ${c / d}`);

let e = 7, f = 5;
console.log(`${e} + ${f} = ${e + f}`);
console.log(`${e} - ${f} = ${e - f}`);
console.log(`${e} * ${f} = ${e * f}`);
console.log(`${e} / ${f} = ${e / f}`);
```
<div align="center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/92710311-0fbe-4c1c-94c9-0229e56e3088">
</div>

```js
function allArithmeics (x, y) {
  console.log(`${x} + ${y} = ${x + y}`);
  console.log(`${x} - ${y} = ${x - y}`);
  console.log(`${x} * ${y} = ${x * y}`);
  console.log(`${x} / ${y} = ${x / y}`);
}

let a = 3, b = 4;
allArithmeics(a, b);

let c = 10, d = 2;
allArithmeics(c, d);

let e = 7, f = 5;
allArithmeics(e, f);
```
<div align="center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/cc017891-c2bd-45f3-b0d6-986cf3250773">
</div>

2. input를 받아 output을 반환(return) 하는 것
   - return이 없다면, undefined 반환
```js
function add(x, y) {
  return x + y; // 값을 반환
}

let z = add(2, 3);

console.log(z);

console.log(add(4, 5));

console.log(add(add(6, 7), add(8, 9)))
```
<div align="center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/23a1b606-d41f-42a6-9949-78c4355621ad">
</div>

```js
function isOdd(x) {
  return !!(x % 2);
}

let num = 12;

console.log(
  `${num} (는)은 ${isOdd(num) ? '홀' : '짝'}수입니다.`
);
```
<div align="center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/67c5667a-829d-4bc3-b3d6-6c2b6fef943c">
</div>

  - input으로 받는 값 : 인수와 인자
```js
function add(x, y) {
  // x, y를 인자 또는 매개변수 (parameter)라 부름
  return x + y;
}

// a, b를 인수(argument)라 부름
let z = add(2, 3);
```

  - 꼭 인자를 받거나 값을 반환하는 것이 없음
```js
let currentTemp = 24.5;

function logCurrentTemp() {
  console.log(`현재 온도는 섭씨 ${currentTemp}도 입니다.`);
}

console.log('반환값 : ', logCurrentTemp());
```
<div align="center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/40e85033-4f51-47d1-b9aa-ef87ca955369">
</div>

    + return문이 정의되어 있지 않으면 undefined 반환
    + console.log 실행 뒤 undefined가 뜨는 이유 

```js
let currentTemp = 24.5;

function logCurrentTemp(temp) {
  console.log(`현재 온도는 섭씨 ${temp}도 입니다.`);
}

console.log('반환값 : ', logCurrentTemp(currentTemp));
```

  - return 문은 꼭 마지막에 선언
```js
function add(x, y) {
  console.log(`${x}와 ${y}를 더합니다.`);
  return x + y;
  console.log(`결과는 ${x + y}입니다.`);
}

console.log(add(2, 7));
```
<div align="center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/14bac4cd-b6e3-43f4-b2c0-c44a44ff39b3">
</div>

```js
function add(x, y) {
  console.log(`${x}와 ${y}를 더합니다.`);
  console.log(`결과는 ${x + y}입니다.`);
  return x + y;
}

console.log(add(2, 7));
```
<div align="center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/29120bf4-4829-4a5b-a2ef-2a9211cf1c67">
</div>

-----
### 호이스팅 (Hoisting)
-----
1. 함수는 실행문보다 나중에 정의하는 것이 가능
2. 단, 변수(let)나 상수(const)는 불가능 (var 제외)
```js
console.log(add(2, 7));

function add(x, y) {
  return x + y;
}
```
<div align="center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/ad15a0d3-1399-4f0b-9ded-e6acf3142ef4">
</div>

3. JavaScript는 실행될 때, 코드를 한 번 전체적으로 확인하여 function을 확인

-----
### 함수 정의 방법
-----
1. 함수 선언
```js
function add(x, y) {
  return x + y;
}

console.log(add(2, 7));
```
<div align="center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/be2f7fdf-8af5-4c29-ac6a-28ab4258dbd8">
</div>

2. 상수나 변수에 함수 대입 (함수도 객체이며, 값 할당 가능)
```js
const subt = function(x, y) {
  return x - y;
};

console.log(subt(7, 2));
```
<div align="center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/cdc02c3a-dc91-4ed7-8413-9aaa7224fd4b">
<img src="https://github.com/sooyounghan/Web/assets/34672301/c8fec351-3300-4111-a64c-9948b6e17551">
</div>

  - 기존의 함수를 재정의 하는 것도 가능
```js
add = function(x, y) {
  console.log(`${x}와 ${y}를 더합니다.`);
  console.log(`결과는 ${x + y}입니다.`);
  return x + y;
};

console.log(add(2, 7));
}
```
<div align="center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/d2753d4f-4caf-44fd-8b33-0b958744db45">
</div>

3. 화살표 함수 (인자를 받고, 값을 반환하는 용도로 많이 사용)
  - 한 줄 안의 값만 반환 시 (return 필요 없음)
```js
const mult = (x, y) => x * y;

console.log(mult(2, 7));
```
<div align="center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/916cd570-50f0-4fee-b2eb-ecc314983b19">
</div>

  - 두 줄 이상 작업 있을 시 (return 필요)
```js
const mult = (x, y) => {
  console.log(`${x}와 ${y}를 곱합니다.`);
  console.log(`결과는 ${x * y}입니다.`);
  return x * y;
};

console.log(mult(2, 7));
```
<div align="center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/36df3d6e-eccf-4c3f-8733-f54afcbadf60">
</div>

    + return문이 없다면 undefined 출력
<div align="center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/26f3174c-5c22-455e-84fe-0e77f546cc32">
</div>  

  - 인자가 하나일 때는 괄호 없이 선언 가능
```js
const pow = x => x ** 2;
console.log(pow(3));
```
<div align="center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/40ea9d49-956b-46c1-84eb-8b553af64dd6">
</div>  

** 화살표 함수는 function 선언 함수와 기능 차이 존재

-----
### 상수나 변수에 함수 대입 및 화살표 함수는 호이스팅 미적용
-----
```js
console.log(div(8, 4));

const div = function (x, y) {
  return x / y;
}
```
<div align="center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/1a7fc947-9b3b-42d4-99c0-f87fc4a91d3a">
</div>  

```js
console.log(div(8, 4));

const div = (x, y) => x / y;
```
<div align="center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/4f0fbc79-d0dd-4cf6-9aa1-cf46c416e83e">
</div>  

: 일반적인 함수 정의 방법의 함수는 엔진의 코드 실행 이전 미리 생성
