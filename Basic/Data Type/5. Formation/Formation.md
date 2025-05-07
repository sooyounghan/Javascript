-----
### 다른 진법들
-----
: ```https://developer.mozilla.org/ko/docs/Web/JavaScript/Guide/Numbers_and_dates#2%EC%A7%84%EC%88%98```
1. 2진법 (Binary)
   - 0b 뒤로 숫자 0, 1를 붙여 표현
```js
[
  0b1,
  0b10,
  0b11,
  0b100,
  0b101
].forEach(i => console.log(i))
```
<div align="center">
<img src="https://github.com/sooyounghan/JavaScript/assets/34672301/e9649d94-123b-42e3-85e6-de148ef99b12">
</div>

```js
console.log(
  0b2 // ⚠️ 토큰으로 인식 - 오류
);
```
<div align="center">
<img src="https://github.com/sooyounghan/JavaScript/assets/34672301/8aedfce0-db8c-4513-a68a-f92f6a3f535f">
</div>

2. 8진법 (Octal)
   - 0o 뒤로 숫자 0 ~ 7을 붙여 표현
```js
[
  0o7,
  0o10,
  0o100,
  0o1000,
].forEach(i => console.log(i))
```
<div align="center">
<img src="https://github.com/sooyounghan/JavaScript/assets/34672301/2aad80a3-1ee8-4430-ba4b-c41610f8bee2">
</div>

```js
console.log(
  0o8 // ⚠️ 토큰으로 인식 - 오류
);
```
<div align="center">
<img src="https://github.com/sooyounghan/JavaScript/assets/34672301/b9ff17bc-0ec6-4a02-b585-0c020f992dad">
</div>

3. 16진법 (Hexadecimal)
   - 0x뒤로 0 ~ 9, A ~ F를 붙여 표현
```js
[
  0x9,
  0xA,
  0xB,
  0xC,
  0xd,
  0xe,
  0xf,
  0x10,
  0xFFFFFF
].forEach(i => console.log(i))
```
<div align="center">
<img src="https://github.com/sooyounghan/JavaScript/assets/34672301/579409a5-581a-470a-93d6-d875384ad765">
</div>

4. 진법 간 변환
  - 2 ~ 36 사이 진법 사용 가능 (toString과 parseInt의 가용 인자 범위)
```js
const num = 123456789;

const binStr = num.toString(2);
const octStr = num.toString(8);
const hexStr = num.toString(16);

console.log(binStr, octStr, hexStr);
```
<div align="center">
<img src="https://github.com/sooyounghan/JavaScript/assets/34672301/87662e54-01fc-411e-a228-b0f8b0e8c131">
</div>

```js
console.log(
  parseInt(binStr, 2),
  parseInt(octStr, 8),
  parseInt(hexStr, 16)
);
```
<div align="center">
<img src="https://github.com/sooyounghan/JavaScript/assets/34672301/a3140960-965f-4c6e-aba3-f77d1dd7f898">
</div>

```js
// 💡 상호변환
console.log(
  parseInt(hexStr, 16).toString(2),
  parseInt(binStr, 2).toString(8),
  parseInt(octStr, 8).toString(16)
);
```
<div align="center">
<img src="https://github.com/sooyounghan/JavaScript/assets/34672301/6dc811f6-9d04-45b3-a891-cc468a0893b9">
</div>

-----
### 비트 연산자
-----
: ```https://developer.mozilla.org/ko/docs/Web/JavaScript/Guide/Expressions_and_Operators#%EB%B9%84%ED%8A%B8_%EC%97%B0%EC%82%B0%EC%9E%90```

```js
let x = 0b1010101010; // 682
let y = 0b1111100000; // 992
```

1. 양쪽 모두 1인 자리에 1
```js
// 양쪽 모두 1인 자리에 1
const bitAnd = x & y;

console.log(bitAnd);
console.log(
  bitAnd.toString(2)
);
```
<div align="center">
<img src="https://github.com/sooyounghan/JavaScript/assets/34672301/46a3fc77-74b1-45a4-a302-3150e72b8395">
</div>


2. 한 쪽이라도 1인 자리에 1
```js
// 한 쪽이라도 1인 자리에 1
const bitOr = x | y

console.log(bitOr);
console.log(
  bitOr.toString(2)
);
```
<div align="center">
<img src="https://github.com/sooyounghan/JavaScript/assets/34672301/82d634ba-fcf2-45e5-b18f-c468919bcd10">
</div>

3. 양쪽이 다른 자리에 1
```js
// 양쪽이 다른 자리에 1
const bitXor = x ^ y;

console.log(bitXor);
console.log(
  bitXor.toString(2)
);
```
<div align="center">
<img src="https://github.com/sooyounghan/JavaScript/assets/34672301/bb1f5b72-4c88-4d6d-b168-14d6c1a142d6">
</div>

4. 각 비트 반전
```js
// 각 비트 반전
console.log(~x);
console.log(
  (~x).toString(2)
);

console.log(~y);
console.log(
  (~y).toString(2)
);
```
<div align="center">
<img src="https://github.com/sooyounghan/JavaScript/assets/34672301/776932e3-3f78-4fc9-8f0d-7fa6844caa17">
</div>

5. 기타
```js
let x = 0b101; // 5

console.log(x.toString(2), x);
```

```js
// 반복 실행해볼 것, 오른쪽 숫자를 늘려 볼 것
x = x << 1;

console.log(x.toString(2), x);
```
<div align="center">
<img src="https://github.com/sooyounghan/JavaScript/assets/34672301/f0dc3a9a-0952-403f-a03e-1fd5f104e9df">
</div>

```js
// 반복 실행해볼 것, 오른쪽 숫자를 늘려 볼 것
x = x >> 1;

console.log(x.toString(2), x);
```
<div align="center">
<img src="https://github.com/sooyounghan/JavaScript/assets/34672301/6c23fb45-641f-46c8-92f4-a662b4bd8281">
</div>
