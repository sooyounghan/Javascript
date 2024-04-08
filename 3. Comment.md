-----
### Comment
-----
1. 사람에게 보여질 목적으로 작성 (즉, 코드에 대한 설명, 추후 진행 사항 등)
2. 단축키 : Ctrl + /
3. 예시
```js
console.log('Hello!');
// This is Comment.
// console.log('주석이라 미실행!');
console.log('World!');
```

<div align="center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/2217e266-675d-4abb-96b2-bc9dce2f451e">
</div>

4. 주석을 해제하면, 자바스크립트 문법 오류로 인해 미실행
5. 주석은 가능한 필요한 만큼만 달되, 많이 다는 것은 좋지 않음

-----
### Comment 방법 예시
-----
1. 한 줄 주석 : //
```js
// 한 줄 주석
console.log('Hello!'); // 여기도 가능합니다.
```

2. 여러 줄 주석 : /* ~ */
```js
/*
 여러 줄 주석
 아직 주석
 이제 끝!
*/ 
console.log('Hello!'); 
```

-----
### Semi-Colon (;)
-----
1. Interpreter Language로 세미 콜론의 강제성을 부여 불가
2. 정확히는 엔진의 ASI(Automatic Semicolon Insertion) 작업에 의해 자동으로 세미콜론를 부여하고 코드 실행
   - 개발자와 의도와 다르게 세미콜론을 부여하거나 부여하지 않는 경우 존재
3. 짧은 Statment에는 세미콜론이 필수적
```js
console.log('Hello!'); console.log('World!');
console.log('Hello!')  console.log('World!') // Error
```
4. ASI는 세미콜론이 없이 줄바꿈이 되면, 다음 구문이 여는 괄호로 시작되면, 세미콜론 미 부착
```js
const x = 1
const y = x

(function () {
  console.log('IIFE')
})()
```
```js
const x = 1
const y = x (function () {
  console.log('IIFE')
})()
```
  - 위와 같이 처리되어 오류 발생 (x를 함수처럼 처리하여 실행)

```js
const x = 1
const y = x

;(function () {
  console.log('IIFE')
})()
```
```js
const x = 1
const y = x;

(function () {
  console.log('IIFE')
})()
```
  - 위와 같이 처리하면 오류 미발생

5. 코드에서 즉석으로 배열을 생성 후, 변수나 상수로 메모리에 넣지 않은 채 forEach을 돌리는 경우
```js
const x = 1
const y = x

[0, 1, 2].forEach(num => {
  console.log(num)
})
```
  : 4번과 동일한 오류 발생
```js
const x = 1
const y = x

;[0, 1, 2].forEach(num => {
  console.log(num)
})
```
```js
const x = 1
const y = x;

[0, 1, 2].forEach(num => {
  console.log(num)
})
```
  - 에러 미발생
    
6. JavaSrcipt에서는 한 실행문마다 붙이는 것이 필수적인 것은 아님
7. 예외적인 상황에서의 오류 방지를 위해 세미콜론 붙이는 것이 좋음
