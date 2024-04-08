-----
### 연산자
-----
1. 산술 연산자
   - 이항 산술 연산자 (+, -, *, /, %, **)
   - 셈 결과 반환
   - 부수 효과 없음
```js
// 값 반환
let x = 10;
let y = x * 10;

console.log(y);
```
<div align="center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/d5f48f47-3e35-4cda-990c-d6e193ee4e23">
</div>

```js
console.log(
  y + 1, // 덧샘
  y - 1, // 뺄셈
  y * 2, // 곱셈
  y / 5, // 나눗셈
  y % 3,  // 나머지
  y ** 2 // 제곱
);
```
<div align="center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/902514ef-0643-4d44-a5c3-e3ce61840f88">
</div>

```js
// 부수효과 없음
console.log(y);
```
<div align="center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/a1cf589e-79b6-43be-9bc2-555bb0f50b74">
</div>

```js
// 널리 사용되는 홀수와 짝수의 판별법
console.log(
  '홀수 ',
  123 % 2,
  55 % 2,
  999 % 2
);
console.log(
  '짝수 ',
  2 % 2,
  100 % 2,
  8 % 2
);
```
<div align="center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/e41d9755-4143-41f3-8c1f-9daf46e478ff">
</div>

2. 괄호의 사용
```js
console.log(
  4 * 1 + 2,
  4 * (1 + 2),
  4 * -(1 + 2),
  -(4 * -(1 + 2))
);
```
<div align="center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/e8a67ba2-ca32-4888-a00a-8b264a6b0a92">
</div>

3. 단항 산술 연산자
```js
let x = 10;

// 값을 반환부터 하고 증가
console.log('1.', x++, x);
```
<div align="center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/9b724fad-0904-44e1-9a97-b7fd51ff3df2">
</div>

```js
// 값을 증가부터 하고 반환
console.log('2.', ++x, x);
```
<div align="center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/8b3a8134-ceaf-4a61-a421-d27ea26a7283">
</div>

```js
let x = 3;
let y = 4;

// 💡 부수효과가 일어나는 시점
console.log(x-- * --y, x, y);
```
<div align="center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/ff6e05eb-d0bd-4c7d-b3fd-56c858dae0a6">
</div>

```js
let x = 1;
console.log(
  +x,
  -x,
  -(-x),
  -(x++),
  -x * -1
);
```
<div align="center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/6d32cd3a-e97d-4768-9cbc-f13e123dd44a">
</div>

4. 문자열을 숫자로 바꿈
```js
console.log(
  +'100',
  -'100',
  +'abc' // 숫자로 변환될 수 없는 문자열 : NaN
);
```
<div align="center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/46173008-8f07-4941-a5cd-8ec0b586440d">
</div>

```js
let x = '100';
console.log(x++, x);
```
<div align="center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/eeac85d5-b603-4524-9a7d-0ca8b6e22fb6">
</div>

```js
let y = '100';
console.log(--y, y);
```
<div align="center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/2497b239-acf2-48b3-a3f5-8c1ee452ad00">
</div>

```js
// 숫자로 변환될 수 없는 문자열 (NaN)
// 첫 번째 값 주의 - 증가 이전에도 변환
let z = 'abc';
console.log(z++, z);
```
<div align="center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/38eee6a8-679f-4c27-8219-8505459b4614">
</div>

4. 할당 산술 연산자 (부수효과)
<div align="center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/23bcde0a-1b1d-4f5d-b502-3793d9212b6a">
</div>

```js
let x = 3;

x += 2;
console.log(x);

x -= 3;
console.log(x);

x *= 12;
console.log(x);

x /= 3;
console.log(x);

x %= 5;
console.log(x);

x **= 4;
console.log(x)
```
<div align="center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/974f42b6-dcd6-4da4-9865-5dc63ca73d6a">
</div>

```js
let y = 25;

console.log(
  y **= 0.5, // 할당된 결과 반환
  y
);
```
<div align="center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/bf37b095-5c59-4c84-b55a-9a018df6e275">
</div>

