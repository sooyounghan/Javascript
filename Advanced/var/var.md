-----
### var
-----
1. let과 const가 생기기 전 변수 선언에 사용되던 자료형
2. 각종 문제점을 갖고 있으므로 오늘날 사용하는 것을 권장하지 않음

-----
### var 특징
-----
1. 선언 없이도 사용 가능 (미리 선언한 부분이 없을 시, var로 만들어짐)
```js
notDeclared = 1; // 미리 선언한 부분이 없을 시 var로 만들어짐
console.log(notDeclared);
```
<div align="center">
<img src="https://github.com/sooyounghan/HTTP/assets/34672301/d6b7d993-c459-4256-995d-e5490bcefffd">
</div>

```js
// num이 var로 선언된 것
for (num of [1, 2, 3]) {
  console.log(num);
}
```
<div align="center">
<img src="https://github.com/sooyounghan/HTTP/assets/34672301/aec5081c-d661-4867-b1c3-350e69287a66">
</div>

2. 재선언 가능 (코딩 중 실수의 여지 발생 가능성 존재)
```js
let a = 1;
let a = 2; // ⚠️ 오류

const b = 1;
const b = 2; // ⚠️ 오류

var c = 1;
var c = 2;
```
<div align="center">
<img src="https://github.com/sooyounghan/HTTP/assets/34672301/71b69ef1-e29b-468a-a30b-70476dadd40e">
</div>

3. 블록 레벨 스코프 무시
```js
let num1 = 1;
{
  let num1 = 2;
  {
    let num1 = 3;
  }
}

console.log(num1);
```
<div align="center">
<img src="https://github.com/sooyounghan/HTTP/assets/34672301/3ec68b63-b0b1-4931-aae5-be2d303d3da4">
</div>

```js
var num2 = 1;
{
  var num2 = 2;
  {
    var num2 = 3;
  }
}

console.log(num2);
```
<div align="center">
<img src="https://github.com/sooyounghan/HTTP/assets/34672301/e5937563-fba5-4740-9ab9-91367f704413">
</div>

  - for문의 스코프도 무시
```js
// for문의 스코프도 무시
for (var i = 0; i < 5; i++) {
  var pow2 = i ** 2;
  console.log(pow2);
}

console.log(i, pow2);
```
<div align="center">
<img src="https://github.com/sooyounghan/HTTP/assets/34672301/2f9ce0c3-3a35-4b2a-991f-f96bb233dec4">
</div>

  - 단, 함수의 스코프는 유효함 : IIFE가 사용되었던 이유
```js
var num3 = 1;

function func1 () {
  var num3 = 2;
  return num3;
}

console.log(num3);
console.log(func1());
```
<div align="center">
<img src="https://github.com/sooyounghan/HTTP/assets/34672301/84ab244e-eecb-4d96-a4b0-82bc002b5fa3">
</div>

-----
### 호이스팅 (Hoisting)
-----
: https://developer.mozilla.org/ko/docs/Glossary/Hoisting

1. 인터프리터가 코드를 실행하기 전 함수, 변수, 클래스 또는 import 선언문을 해당 범위의 맨 위로 끌어올리는 것처럼 보이는 현상
```js
console.log(hoisted1); // ⚠️ 오류
```
<div align="center">
<img src="https://github.com/sooyounghan/HTTP/assets/34672301/647dd490-5a09-4ca2-87ce-9ee3979d8f00">
</div>

```js
console.log(hoisted1); // 💡 오류발생 X, 대신 undefined 반환

var hoisted1 = 'Hello'; // 엔진이 실행될 때, var hosited1을 맨 위로 끌어올림 (초기화는 아직 진행되지 않았으므로 undefined)

console.log(hoisted1)
```
<div align="center">
<img src="https://github.com/sooyounghan/HTTP/assets/34672301/02095a00-5dbc-4caa-bdb6-11e70b549192">
</div>

```js
console.log(hoisted2); // ⚠️ 오류

let hoisted2 = 'Hello';

console.log(hoisted2)
```
<div align="center">
<img src="https://github.com/sooyounghan/HTTP/assets/34672301/da1db144-e868-4b53-940e-6f87730181ac">
</div>

2. 엄연히는 let / const도 호이스팅되지만 undefined로 초기화되지 않는 것
3. 단, 이들은 초기화되기 이전의 영역 : TDZ에 속함 (https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Statements/let#%EC%8B%9C%EA%B0%84%EC%83%81_%EC%82%AC%EA%B0%81%EC%A7%80%EB%8C%80)
  - TDZ (시간상 사각지대, Temproal Dead Zone) : 변수 스코프의 맨 위에서 변수의 초기화 완료 시점까지 변수가 존재하는 곳
  - 따라서, ReferenceError가 발생
    
* var는 다양한 상황에서 예기치 못한 문제를 야기하므로 더 이상 사용하지 않도록 하는 것이 좋음
