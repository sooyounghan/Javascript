참고자료 : https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Statements/if...else

-----
### if 문
-----
1. 주어진 조건에 따라 수행 여부를 결정하는 문장
2. 괄호 안에 Boolean 또는 Boolean형으로 평가될 수 있는 Truthy, Falsy가 가능
  - True 값이면, 문장 수행

```js
const open = true;

// 한 줄 코드
if(open) console.log('영업중입니다.');
```
<div align="center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/ab32a2f7-d292-4fd9-87d2-7fc086b4e05c">
</div>

```js
// 여러 줄 코드 : 블록문 사용
if (open) {
  console.log('환영합니다.');
  console.log('즐거운 쇼핑하세요!');
}
```
<div align="center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/25c87946-f4d1-4095-8802-ffa7ebc5b6c3">
</div>

-----
### if ~ else 문
-----
1. if문이 true나 truthy 값이면, 수행
2. false나 falsy 값이면, else문 수행

```js
const x = 20;

if (x % 2) {
  console.log('홀수입니다.');
} else {
  console.log('짝수입니다.');
}
```
<div align="center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/85d675f6-4fdb-44a3-a70a-1191a3c31e16">
</div>

-----
### 중첩 사용
-----
```js
const x = 22;

if (x % 4) {
  if (x % 2) {
    console.log('홀수입니다.');
  } else {
    console.log('짝수입니다.');
  }
} else {
  console.log('4의 배수입니다.');
}
```
<div align="center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/91166385-f6b7-4a78-9852-769c3daf2e41">
<img src="https://github.com/sooyounghan/Web/assets/34672301/dbc7ed95-b033-4bc1-a8ae-16b6802beda9">
</div>

-----
### if ~ else if ~ 문
-----
```js
const x = 21;

if (x % 2) {
  console.log('홀수입니다.');
} else if (x % 4) {
  console.log('짝수입니다.');
} else {
  console.log('4의 배수입니다.');
}
```
<div align="center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/592f3999-519d-41fc-8351-a562cd2e10cc">
</div>

-----
### return 문 : 함수 실행을 완전히 종료
-----
```js
function evalNum() {
  const x = 21;

  if(x % 2) { // x가 2로 나눈 나머지가 true
    console.log('홀수입니다.');
    return; // 통과한 후, 종료
  }

  if(x % 4) { // x가 4로 나눈 나머지가 true
    console.log('짝수입니다.');
    return; // 통과한 후, 종료
  }

  console.log('4의 배수입니다.'); // 위의 두 조건 모두 false
}

evalNum();
console.log('블록문 바깥');
```



