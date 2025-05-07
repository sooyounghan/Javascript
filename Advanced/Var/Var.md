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
