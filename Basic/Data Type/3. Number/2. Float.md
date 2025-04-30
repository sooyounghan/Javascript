-----
### 자바스크립트의 number 자료형은 부동 소수점 (Float Number) 이용
-----
-----
< 부동 소수점 >
 - 예) 1001.101 = 9.625
 - 총 32bit 중, 맨 앞의 1bit는 양수 / 음수
 - 다음 8bit(10000001)는 소숫점을 몇 칸을 움직일지 결정 (130-127 = 3)
 - 23자리는 다음 오는 부분을 할당
-----

1. IEEE 754 표준 double 형식 (64bit)
2. 자바스크립트에는 기본 정수 자료형이 없음
   - 내장 객체 (BigInt)

```js
console.log(
  0.1 + 0.2,
  0.1 + 0.2 === 0.3
);
```
<div align="center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/5da4a1d5-670e-4050-94bb-f37863a341fd">
</div>

```js
let x = 0.1 * 10;
let y = 0.1 + 0.1 + 0.1 + 0.1 + 0.1
 + 0.1 + 0.1 + 0.1 + 0.1 + 0.1;

console.log(
  x, y, x === y
);
```
<div align="center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/81ce275f-fbc5-4aef-89c2-40db3bea207f">
</div>

```js
console.log(
  0.2 * 0.7,
  0.4 * 3,
  0.9 - 0.6,
  0.9 - 0.3
);
```
<div align="center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/cb3e0782-1094-4deb-be4c-e0b851082adb">
</div>


3. 2의 거듭제곱으로 나눈 수의 계산은 정확
```js
// ⭐️ 2의 거듭제곱으로 나눈 수의 계산은 정확
console.log(
  0.25 * 0.5,
  0.5 + 0.25 + 0.125 + 0.125,
  0.0625 / 0.25
);
```
<div align="center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/eceaaf5a-8698-4a40-88f8-bf688a82efe8">
</div>


4. 정확한 계산이 필요할 때는 라이브러리 활용
   
