-----
### 전역 객체 (Global Object)
-----
1. 코드로 선언하거나 하지 않아도 전역 범위에 항상 존재하는 객체
2. https://developer.mozilla.org/ko/docs/Glossary/Global_object

< Broswer >
  
```js
console.log(this);
```
<div align="center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/55b7a41e-dbe8-431e-912b-692de6a4dedf">
</div>

```js
console.log(
  this === window,
  window === self,
  self === frames
);
```
<div align="center">
</div>

  - this는 브라우저에서 window, self, frams과 동일
    
```js
console.log(globalThis);
```
<div align="center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/8d4868f7-24bf-4d45-99ed-c9515f0ea609">
</div>

< Node.js >
```js
// Node.js로 문서 실행 시 this는 전역 객체를 가리키지 않음
console.log(this);
```
<div align="center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/6de3b967-889b-4f9c-b338-c679e1337ded">
</div>

```js
console.log(global);
```
<div align="center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/f60022c6-009c-40f3-9756-65c15bb0d0fc">
</div>

  - global이 Node.js에서의 전역 객체를 의미

```js
console.log(globalThis);
```
<div align="center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/814e3f38-30f3-4483-b846-a6aca09eb4bb">
</div>

3. globalThis : 통일된 this 식별자
4. 전역 객체에 포함되는 것
   - 표준 빌트인 객체 (Standard Built-In Objects)
   - 호스트 객체 (Host Objects) : 환경에서 제공하는 기타 객체 (Broswer의 WEB API, Node.js API 등)
   - 브라우저 한정 : 전역으로 설정된 var 변수와 전역 함수

  ```js
var myGlobalVar = 1;
const myGlobalConst = 1;

function myGlobalFunc() { };

console.log(
  globalThis.myGlobalVar,
  globalThis.myGlobalConst,
  globalThis.myGlobalFunc
);
```
<div align="center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/b2dd8609-bed0-43b4-b840-d3658c418025">
</div>

-----
### 표준 빌트인 객체 (Standard Built-In Objects) = 표준 내장 객체
-----
: https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects
1. ECMA Script 사양에 정의된 객체들로, 어떤 환경에서든 사용 가능
2. 전역 프로퍼티로 제공됨 (globalThis 등을 붙이지 않고 바로 사용 가능)
3. Node.js에서는 globalThis 출력 시, 표준 빌트인 객체들은 출력하지 않음
   - Node.js API만 표시
   - 물론, 표준 빌트인 객체를 확인하면 나옴
   
```js
// 그러나 요소들로 갖고 있는 것은 확인 가능
console.log(globalThis.Infinity);
console.log(globalThis.isNaN);
console.log(globalThis.Object);

console.log(Infinity);
console.log(isNaN);
console.log(Object);
```
<div align="center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/dce9742a-eb41-4645-9319-6907b91417fa">
</div>

-----
### 래퍼 객체 (Wrapper Obejct)
-----
```js
const str = 'abcde';
console.log (
  str.length,
  str.toUpperCase(),
  str[0]
);
```
<div align="center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/2fcbd13a-20d3-4296-a95d-f5e4d703fa33">
</div>

```js
const num = 123.4567;
console.log(
  num.toString(), // number를 string으로 변환
  num.toFixed(2) // 소수점 n번째까지 표시되도록 반올림
);
```
<div align="center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/8cf18326-6a30-4111-b204-0ffa828cfafc">
</div>

  - 원시값이 어떻게 프로퍼티를 가지고 있는가?

```js
const str = new String('abcde');
const num = new Number(123.4567);
const bool = new Boolean(true);

console.log(typeof str, str);
console.log(typeof num, num);
console.log(typeof bool, bool);
```
<div align="center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/0e2aa696-8698-4504-8cd2-4f013e265a0e">
</div>

1. Number, String, Boolean 등은 표준 빌트인 객체에 속하는 래퍼 객체
   - 원시값을 필요 시, 래퍼 객체로 감싸서(Wrap), 이의 인스턴스로 만들어 기능 실행
   - 원시값에서 객체를 사용하듯, 해당 래퍼 객체의 프로퍼티를 호출할 때 래핑(Wrapping) 발생

2. 해당 기능을 사용한 후에는 원시 객체로 돌아감 (메모리 절약 위함)
```js
const str = 'abcde';
console.log(str.length);
console.log(typeof str, str);
```
<div align="center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/8f683ea7-22e7-40ec-890a-f5409b49ffe2">
</div>

3. valueOf 함수 : 래퍼 객체의 인스턴스에서 원시값 반환
   - Wrapper Class의 Prototype에 valueOf 존재
   - 즉, 원형인 Object의 valueOf() 상속
```js
const str = new String('abcde');
const num = new Number(123.4567);
const bool = new Boolean(true);

console.log(str.valueOf());
console.log(num.valueOf());
console.log(bool.valueOf());
```
<div align="center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/628f2cbe-651c-4080-9ccf-b9fb6d78efb1">
</div>
