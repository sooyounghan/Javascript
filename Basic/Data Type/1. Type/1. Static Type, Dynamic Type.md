-----
### 자바스크립트의 언어 특징
-----
1. 동적 타입을 가진 언어 (인터프리터 언어의 특징)
   - 정적 언어 : 컴파일러 언어의 특징 (변수 등에 지정된 값을 변경 불가)
2. 특정 값이 할당된 변수에, 그와 다른 자료형의 값을 넣는 것이 가능
3. 자유롭지만, 그만큼 관련 오류들에 취약
   - 컴파일 언어는 컴파일 과정에서 자료형의 오류도 검수
```js
let job = '학생';
let age = 17;

console.log(job, age);
console.log(typeof age);

// 숫자 값이 들어있던 age에 문자열 값을 넣음
age = '열일곱';

console.log(age);

console.log(typeof age);
```
<div align="cetner">
<img src="https://github.com/sooyounghan/Web/assets/34672301/82a7f2d7-1d79-4806-a305-ba726ac3122e">
</div>

-----
### 자료형의 다름으로 일어날 수 있는 오류
-----
1. 특정 자료형에 대해서만 사용될 수 있는 기능 (런타임 오류)
```js
// 주어진 문자열을 대문자로 바꾸는 함수
// 다른 자료형에 대한 예외처리 없음
function getUpperCase(str) {
  return str.toUpperCase();
}

console.log(getUpperCase('hello'));
```
```js
// ⚠️ 오류 발생!
console.log(getUpperCase(1));
```
<div align="center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/4d763acf-a033-4e93-9040-b44aa3ca162f">
<img src="https://github.com/sooyounghan/Web/assets/34672301/b81bf8df-faca-4a64-82e3-a6dfe30b24d4">
</div>

2. 의도와 다른 연산 (논리 오류)
```js
1 + 1
```
```js
'1' + 1 // '1'은 문자열이므로 '11' 문자열로 인식
````
<div align="center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/726ea770-b158-4f56-a6cc-2815ed3f7b8a">
</div>


