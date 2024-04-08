-----
### 숫자 자료형으로 표현되는 것
----
1. 양과 음의 정수와 실수
```js
// 자바스크립트에는 정수와 실수의 자료형이 따로 있지 않음
let integer = 100;
let real = 1.234;
let negative = -5.67;

console.log(
  typeof integer,
  typeof real,
  typeof negative
);
```
<div align="center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/b6b8a5cc-aa15-4b23-8cfa-1f23e1cf03f6">
</div>

2. 무한대
```js
let x = 1 / 0;
console.log(x, typeof x);
```
<div align="center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/816cb24e-7544-4bb3-8846-fbda866d64ba">
</div>

```js
// 무한대에는 양음이 있음
console.log(-x, typeof -x);
```
<div align="center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/3f97efd7-f843-49a5-b612-e0e797e86e8b">
</div>

```js
let y = -1 / 0;
console.log(y, typeof y);
```
<div align="center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/29850839-7ff3-487b-8f7d-c1ac03adefad">
</div>

```js
let z = Infinity;
console.log(z, typeof z);
```
<div align="center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/6e590ea7-74ba-41ce-8ac6-c5a4162e4c22">
</div>

3. 숫자가 아닌 것
```js
let x = 1 / 'abc';
let y = 2 * '가나다';
let z = NaN;

console.log(x, typeof x);
console.log(y, typeof y);
console.log(z, typeof z);
```
<div align="center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/4292e294-b8a9-47e5-b7c5-01960cb05936">
</div>

  - 숫자가 들어와야 하는 자리인데, 들어오지 못하므로 NaN 반환
  - 자료형은 숫자가 들어와야 하므로 Number
  - NaN은 음수여도 그 값이 NaN

4. 주어진 값이 NaN인지 확인하는 방법
```js
let x = 1 / 'abc';

console.log(
  x,
  x == NaN,
  x === NaN,
  isNaN(x), // 숫자가 아닐 시 true
  Number.isNaN(x) // 보다 엄격한 버전
);
```
<div align="center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/583ed291-6a3c-423a-baf5-b11faba513b6">
</div>

  - ==과 ===으로는 NaN의 일치 여부 확인 불가
  - NaN 여부 확인 : isNaN(), Number.isNaN()
     
5. isNaN과 Number.isNaN의 차이
<div align="center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/1ddea934-07ca-4e92-8868-4a125e9e783a">
</div>
  - Number.isNaN() : 해당 인자를 숫자를 변환하려고 시도하고, 이 작업에서 숫자로 변환 불가하면, NaN으로 간주

```js
console.log(
  typeof '1', isNaN('1'), Number.isNaN('1')
); // 특정 숫자로 변환 가능한 문자
```
<div align="center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/f3c269ad-af1a-49aa-bb8f-391bb240c527">
</div>

```js
console.log(
  typeof true, isNaN(true), Number.isNaN(true)
); // true는 1, false는 0으로 변환됨
```
<div align="center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/e9251b1f-1480-4cf7-997b-83ba7b070328">
</div>

```js
console.log(
  typeof 'a', isNaN('a'), Number.isNaN('a')
); // ⚠️ 특정 숫자로 변환 불가인 문자의 경우 차이
```
<div align="center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/e414dc6d-3dcf-4caa-967b-aee70e051a98">
</div>

```js
console.log(
  typeof (1/'a'), isNaN(1/'a'), Number.isNaN(1/'a')
); // NaN값인 경우
```
<div align="center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/6aa28a5f-4950-4914-8a43-0d4c89a47666">
</div>


