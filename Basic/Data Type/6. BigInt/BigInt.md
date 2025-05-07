-----
### Number.MAX_SAFE_INTEGER
-----
: ```https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/BigInt```
1. 더 큰 정수를 다루기 위한 자료형
2. 매우 큰 정수를 다뤄야 하는 특수한 경우 사용
```js
console.log(
  Number.MAX_SAFE_INTEGER
);
```
<div align="center">
<img src="https://github.com/sooyounghan/JavaScript/assets/34672301/8d0dc881-1c4f-4e44-bdd7-1c15dfda8d5a">
</div>

3. number 타입으로 안정적으로 표현할 수 있는 가장 큰 정수 : 9007199254740991 (2^53 - 1)
```js
for (let i = 0; i < 100; i++) {
  console.log(Number.MAX_SAFE_INTEGER + i);
}
```
  - 해당 숫자 이상으로 표현 불가함을 알 수 있음
<div align="center">
<img src="https://github.com/sooyounghan/JavaScript/assets/34672301/124e5205-481f-4253-a47e-9a8b918f51fe">
</div>

-----
### BingInt
-----
: 자바스크립트의 부동소수점 방식으로 표현이 불가능한 가장 큰 숫자 외의 범위를 표현할 때 사용
1. BigInt 생성 방법
```js
const bigInt1 = 9007199254740991n; // 끝에 n을 붙임
const bigInt2 = BigInt(9007199254740991);
const bigInt3 = BigInt('9007199254740991');
const bigInt4 = BigInt(0x1fffffffffffff) // 9007199254740991 (16진수)

console.log(
  bigInt1 === bigInt2,
  bigInt2 === bigInt3,
  bigInt3 === bigInt4
);

console.log(typeof bigInt1);

for (let i = 0; i < 100; i++) {
  console.log(bigInt1 + BigInt(i));
}
```
<div align="center">
<img src="https://github.com/sooyounghan/JavaScript/assets/34672301/5c04356c-5d1c-486c-b5f4-bf8028ba0afc">
</div>

2. 특징
   - 일반 number 타입과 산술 (+, -, *, /, %, **) 연산 불가
   - BigInt 타입과는 가능
```js
console.log(
  1n + 1
);

console.log(
  1n + 1n
);
```
<div align="center">
<img src="https://github.com/sooyounghan/JavaScript/assets/34672301/f7aecc46-8838-4837-b4f1-fc29b5804cdb">
</div>

```js
// 양쪽 모두 BigInt로 변환하여 계산하는 방법 사용
const calcAsBigInt = (x, y, op) => {
  return op(BigInt(x), BigInt(y));
}

console.log(
  calcAsBigInt(1n, 1, (x, y) => x + y)
);
```
<div align="center">
<img src="https://github.com/sooyounghan/JavaScript/assets/34672301/0c9930b0-536e-4ce2-a6fe-b720cfaf44fe">
</div>

  - 비교 연산 가능
```js
console.log(
  1n === 1, // 타입은 다름
  1n == 1,
  1n < 2,
  1n >= 0,
  2n < 1
);
```
<div align="center">
<img src="https://github.com/sooyounghan/JavaScript/assets/34672301/a77e9372-9578-463a-b4d9-c6a091b00411">
</div>

  - number 숫자와 섞여 정렬 가능
```js
console.log(
  [4n, 7, 6n, 3, 1, 5, 9, 2n, 8n]
  .sort((a, b) => a > b ? 1 : -1)
);
```
<div align="center">
<img src="https://github.com/sooyounghan/JavaScript/assets/34672301/ca10cc38-0e1d-4868-a678-0f6e6488bfab">
</div>

  - boolean으로 변환(truthy, falsy)되는 연산 가능
```js
console.log(
  !!(0n),
  !!(1n)
);

0n ? console.log('참') : console.log('거짓');
1n ? console.log('참') : console.log('거짓');
```
<div align="center">
<img src="https://github.com/sooyounghan/JavaScript/assets/34672301/99b1d484-ec7b-4271-89f8-7f10bce4a044">
</div>

  - 소수점 아래는 버림
```js
console.log(
  5n / 2n
);
```
<div align="center">
<img src="https://github.com/sooyounghan/JavaScript/assets/34672301/d967dbb6-c395-4d6c-9ef6-b91669460633">
</div>

  - Math의 정적 메서드 사용 불가
```js
console.log(
  Math.max(1n, 2n)
);
```
<div align="center">
<img src="https://github.com/sooyounghan/JavaScript/assets/34672301/575f19b4-bebd-4fac-881b-3d6fab09b435">
</div>

  - number로 변환 가능하나, 정확성 유실 주의
```js
console.log(
  Number(1n),
  Number(9007199254740993n) // 정확성 유실
);
```
<div align="center">
<img src="https://github.com/sooyounghan/JavaScript/assets/34672301/84cf4695-3f01-4d87-be6a-897db3f644af">
</div>

