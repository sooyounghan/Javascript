-----
### Boolean
-----
```js
console.log(true, typeof true);
console.log(false, typeof false);
```
<div align="center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/b935586e-528d-4053-b796-0bba8656e94c">
</div>

```js
let a = 1 === 2;
let b = 'abc' !== 'def'
let c = a !== b;
let d = typeof a === typeof b === true;

console.log(a, typeof a);
console.log(b, typeof b);
console.log(c, typeof c);
console.log(d, typeof d);
```
  - typeof a === typeof b === true
    + 1번 : typeof a === typeof b
    + 2번 : typeof a === typeof b의 결과에 대해 === true
      
<div align="center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/a6d36546-d8e7-4d58-bb5b-f9a396de2f8f">
</div>

-----
### Boolean 연산자
-----
1. 부정 연산자
```js
console.log(
  true, !true, false, !false
);

console.log(
  true, !true, !!true, !!!true
);

console.log(
  false, !false, !!false, !!!false
);
```
<div align="center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/f93e4664-7146-4e53-a898-784f547f69ed">
</div>

```js
console.log(
  true === !false,
  !(1 == '1'),
  !(1 === '1'),
  !(typeof false === 'boolean')
);
```
<div align="center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/8cb2f39a-6ef5-4d6e-85c5-0ab0dfd916f0">
</div>

2. AND / OR 연산자
  - && : AND (양쪽 모두 true이어야 true)
```js
console.log(
  true && true,
  true && false,
  false && true,
  false && false,
);
```
<div align="center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/7c88c35c-3c98-430d-8e4c-d81508ee58eb">
</div>

  - || : OR (한 쪽 이라도 true이면 true)
```js
console.log(
  true || true,
  true || false,
  false || true,
  false || false,
);
```
<div align="center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/1ef99aeb-4997-46f2-b3ef-45f9cc0ba8d9">
</div>

```js
let x = 14;
// x = 6;
// x = 25;

console.log(
  (x > 10 && x <= 20) || x % 3 === 0
);
```
<div align="center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/96a855fe-165a-40d2-96ba-2b62ca65441f">
</div>

```js
// 💡 드 모르간의 법칙
let a = true;
// a = false;
let b = true;
// b = false;

console.log(
  !(a && b) === (!a || !b),
  !(a || b) === (!a && !b)
); // 💡 항상 true
```
<div align="center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/7c71da08-6049-4553-89dc-31ab21ef5ea1">
</div>

2. 단축 평가 (Short Circuit)
   - && : 앞의 것이 false이면, 뒤의 것을 실행하지 않음 (= 즉, 앞의 것이 true이면, 뒤의 것 실행)
   - || : 앞의 겂이 true이면, 뒤의 것을 실행하지 않음 (= 즉, 앞의 것이 false이면, 뒤의 것 실행)
   - 즉, 연산 부하가 적은 코드를 앞에 작성하는 것이 좋음 (Resource 절약)
```js
let error = true;
// error = false;

// 앞의 것이 true일 때만 뒤의 코드 실행
error && console.warn('오류 발생!');

// 앞의 것이 false일 때만 뒤의 코드 실행
error || console.log('이상 없음.');
```
<div align="center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/430f884e-d5c4-4470-9092-c3992242113d">
</div>

```js
let x = true;
// x = false;

// ⭐️ &&, || 연산자는 값 자체를 반환
let y = x && 'abc';
let z = x || 123;

console.log(y, z);
```
  - 'abc', 123은 truthy이므로, 조건문 등에서 true로 인식
  - 따라서, boolean으로 반환하는 &&과 ||의 반환 값으로 나올 수 있음
    
<div align="center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/461ff197-43da-4b7c-8b32-ce7ee8db39ec">
</div>

3. 삼항 연산자 : (  ? : )
  - https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Operators/Conditional_Operator
```js
let x = true;
// x = false;

let y = x ? '참입니다.' : '거짓입니다.';
console.log(y);
```
<div align="center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/89ac2554-f826-4e24-aef8-a64723cfefa6">
</div>

```js
let num = 103247;

console.log(
  'num은 3의 배수' +
  (num % 3 === 0 ? '입니다.' : '가 아닙니다.')
);
```
<div align="center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/2f658d8c-0d29-47ee-8984-da982c75796b">
</div>

```js
let error = true;
//error = false;

error 
  ? console.error('오류 발생!') 
  : console.log('이상 없음');
```
<div align="center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/858b0d42-98d1-4392-9178-6d49819de0f7">
</div>

  - console.error()나 console.log()는 undefined를 반환하므로 다음과 같이 undefined
  
-----
### Truthy vs Falsy
-----
1. true 또는 false로 평가되는 값들
   - Truthy 목록 : https://developer.mozilla.org/ko/docs/Glossary/Truthy
   - Falsy 목록 : https://developer.mozilla.org/en-US/docs/Glossary/Falsy

2. Truthy (참 같은 값)
   - 0이 아닌 숫자
   - ' ', '0'
   - (-)Infinity [단 NaN은 제외]
   - 빈 객체, 빈 배열
  
```js
console.log(
  1.23 ? true : false,
  -999 ? true: false,
  '0' ? true : false,
  ' ' ? true : false,
  Infinity ? true : false,
  -Infinity ? true : false,
  {} ? true : false,
  [] ? true : false,
);
```
<div align="center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/b12f60db-3888-4cf3-bc98-eb2637d670f6">
</div>

```js
// ⚠️ true와 `같다`는 의미는 아님
console.log(
  1.23 == true,
  ' ' == true,
  {} == true
);
```
<div align="center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/32de85aa-a386-4211-9226-22610dc2c808">
</div>

3. Falsy (거짓 같은 값)
   - (-)0
   - ''와 같은 빈 문자열
   - null, Undeifined, NaN
   
```js
console.log(
  0 ? true : false,
  -0 ? true : false,
  '' ? true : false,
  null ? true : false,
  undefined ? true : false,
  NaN ? true : false,
);
```
<div align="center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/837ba6b7-4d6e-452d-9e20-b7735f5046c5">
</div>

```js
// 💡 어떤 값들은 false로 타입변환됨
console.log(
  0 == false,
  0 === false,
  '' == false,
  '' === false
);
console.log(
  null == false,
  undefined == false,
  NaN == false,
);
```
  - 0과 ''은 false은 동일한 값이지만, 자료형이 틀리므로 ===는 false
<div align="center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/4ba11466-4027-4cfb-8c35-14220f7bc1fb">
</div>

4. 예시
```js
let x = 0;
let y = 1;

x && x++;
y && y++;

console.log(x, y);
```
  - x=0은 false로 인식하여, x++는 미실행
  - y=1은 true로 인식하여, y++ 실행
<div align="center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/e8690378-96ad-4566-9c5b-71f654ed5bb1">
</div>


```js
let x = 2;
let y = 3;

console.log(
  x % 2 ? '홀' : '짝',
  y % 2 ? '홀' : '짝'
);
```
<div align="center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/d03c4946-e2bd-4e65-99ad-4f9e1d6871b7">
</div>

```js
let x = '';
let y = '회사원';
let z = x || y;

console.log(z);
```
<div align="center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/319bce5e-8e25-4a32-8015-c009a10e2b33">
</div>

```js
x = x || '단기알바';
y = y || '단기알바';

console.log(x, y);
```
<div align="center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/c01202c6-0903-4055-9832-1c5e93d88702">
</div>

< Boolean으로 직접 변환 >
```js
// 한 번 부정
console.log(
  !1, !-999, !'hello',
  !0, !'', !null
);
```
<div align="center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/498541c3-974f-4084-9e52-46c9d75b763f">
</div>

```js
// ⭐️ 두 번 부정하여 해당 boolean값으로
console.log(
  !!1, !!-999, !!'hello',
  !!0, !!'', !!null
);
```
<div align="center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/dccfe8f3-a5a0-4485-94ff-0281f8d7b8d7">
</div>

```js
let x = 123;

console.log(
  'x는 홀수인가?',
  !!(x % 2)
);
```
<div align="center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/6e5a8225-d2ac-4d79-9ac1-90fe03045a77">
</div>
