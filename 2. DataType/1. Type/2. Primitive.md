-----
### 자바스크립트의 원시 자료형 (Primitive Data Type)
-----
1. 쉽게 말하면, 값 하나만 담는 단순 자료형
```js
const a = true, b = 123.45, c = '안녕하세요!';
````

2. typeof 연산자 : 뒤에 오는 값의 자료형 반환
  - 반환 : 쉽게 말하자면, 해당 코드 부분을 반환 값으로 바꿔쓸 수 있다는 것
```js
console.log(a, typeof a);
console.log(b, typeof b);
console.log(c, typeof c);
```
<div align="center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/76f1332f-8d57-4fc8-a2f3-b3550f8ede92">
<img src="https://github.com/sooyounghan/Web/assets/34672301/746f88f3-8b50-4703-ba2c-eb162fc1cad2">
</div>

```js
let d;
consold.log(d, type of d);
```
```js
d = null;
console.log(d, typeof d);
```
<div align="center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/8c32b75f-7a3d-4525-bed7-27bf613c5bd4">
</div>

```js
const e = Symbol('hello');
console.log(typeof e);
```
<div align="center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/e3ea85e7-be6c-4b4e-94bd-faec5eeb5724">
</div>

-----
### Boolean
-----
```js
let isEmployed = true;
let isMarried = false;

console.log('직업 있음 : ', isEmployed);
console.log('기혼 : ', isMarried);
```
<div align="center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/3984082b-753e-4be4-9305-f2faa0e81118">
</div>

1. 참 또는 거짓 (true or false) : 상반된 둘 중 하나의 값을 담을 수 있음
2. 직접 할당되기보다 반환값으로 프로그램 곳곳 활용

```js
const a = 1 > 2;
const b = 1 < 2;

console.log(a, typeof a);
console.log(b, typeof b);
```
<div align="center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/446aa078-4cb6-4487-aca7-95a3771435e2">
</div>

-----
### Number
-----
```js
let integer = 100;
let real = 12.34;
let negative = -99;

console.log(integer, real, negative);
```
<div align="center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/d2b6d8d5-4826-48e2-801f-59abf6c3ce13">
</div>

1. 자바스크립트는 정수와 실수 구분이 없음 (정수도 실수로 처리)
2. 정수는 2^53 - 1까지 안정적 표현 가능 (더 큰 정수는 BigInt로 처리)

-----
### String
-----
```js
let first_name = "Brendan";
let last_name = "Eich";
let description = `미국의 프로그래머로 자바스크림트 언어를 만들었으며 모질라의 CEO와 CTO를 역임했다.`;

console.log(first_name, last_name);
console.log(description);
```
<div align="center">
<img width="454" alt="20240401_100857" src="https://github.com/sooyounghan/Web/assets/34672301/9e78cc9e-d191-4bff-85c4-0fe2af5d750c">
</div>

1. 큰따옴표, 작은따옴표, 또는 백틱(`)으로 둘러싸인 데이터
2. 유니코드의 모든 문자열 표현 가능

```js
console.log(
  typeof(typeof true),
  typeof(typeof 123.45),
  typeof(typeof 'Hello'),
);
```
<div align="center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/9ad761c3-1085-4e74-b28f-977e897d8e56">
</div>

  - typeof의 반환값은 문자열
  - 즉, typeof true은 'boolean'이라는 문자열 반환
  - typeof 123.45은 'number'라는 문자열 반환
  - typeof 'Hello'는 'String'이라는 문자열 반환
    
-----
### Undefined
-----
```js
let x;
console.log(typeof x);
```
<div align="center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/fe6eda36-cf4e-4e20-ad83-686ccfa3ce9d">
</div>

1. 값이 부여되지 않은 상태라는 의미
2. 하지만, undefined도 값임을 주의
3. 아무 것도 반환하지 않는 구문은 undefined을 반환
```js
let x = 1;
```
<div align="center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/40da54df-351d-4cb7-bee8-5f6a98440da0">
</div>

  - let x = 1이라고 선언만 한 것이지, 무엇인가를 반환하지 않으므로 undefined

-----
### null
-----
```js
let x;
console.log('값 넣기 전', typeof x);

x = null;
console.log('null값 넣은 후', typeof x);
```
<div align="center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/89cbc600-23aa-4d62-8640-2d8da72afe60">
<img src="https://github.com/sooyounghan/Web/assets/34672301/515fa0b3-dd03-4251-8c3d-a626c44e2180">
</div>

```js
let x = 1;
console.log('변경 전', x);

x = null;
console.log('변경 후', x);
```
<div align="center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/0fc270da-eea9-47f7-8e78-bb042e8231d3">
<img src="https://github.com/sooyounghan/Web/assets/34672301/59165dcc-8a98-4053-b3df-61d228a7aa9e">
</div>

1. 의도적인 빈 값 의미
2. 하지만, null값 또한 값을 의미 (즉, 비어있다라는 의미의 값)
3. object(객체) 등이 들어있거나 object가 반환되어야 하지만 없을 때 주로 사용
   - 객체 생성 실패한 경우 대신 반환

4. 주의 : typeof가 object를 반환 (초기오류 : 객체는 원시타입이 아님)
```js
let x = null;
console.log(typeof null, typeof x);

// null 여부는 아래와 같이 확인할 것
console.log(x === null);
```
  - null 확인 연산자 : ===
<div align="center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/7238c71f-3263-4294-9a08-3c12cf086bce">
<img src="https://github.com/sooyounghan/Web/assets/34672301/551a4213-9ec4-4469-bf76-52ca850a7f72">
</div>
