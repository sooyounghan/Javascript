-----
### 기타 연산자
-----
1. 쉼표 연산자 : 왼쪽부터 차례대로 실행, 마지막 것 반환
```js
let x = 1, y = 2, z = 3;
console.log(x, y, z);

// 마지막으로 실행한 것 반환
console.log(
  (++x, y += x, z *= y)
);
```
  - 즉 console.log내 전체가 실행되지만, 반환 값은 z *= y만 반환

<div align="center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/e9997349-4759-473e-b190-93d183202cc4">
</div>

2. ?? : null 병합 연산자
   - || 와 달리, falsy가 아닌 null 또는 undefined만 대체
```js
let x;
x ?? console.warn(x, 'x에 값이 없습니다.');

x = 0;
x ?? console.warn(x, 'x에 값이 없습니다.');

x = null;
x ?? console.warn(x, 'x에 값이 없습니다.');
```
<div align="center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/4e22156b-138e-43cb-846a-48c2ec732bc1">
</div>

```js
let a = false;
let b = 0;
let c = '';
let d = null;
let e;

console.log(
  a ?? '기본값',
  b ?? '기본값',
  c ?? '기본값',
  d ?? '기본값',
  e ?? '기본값',
);
```
<div align="center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/f44be2cf-f8e9-44d6-aeca-15b1a0a93ace">
</div>

  - 활용 예
```js
let baby1 = '홍길동';
let baby2; // 아직 이름을 짓지 못함

const nameTag1 = baby1 ?? '1번 아기';
const nameTag2 = baby2 ?? '2번 아기';

console.log(nameTag1, nameTag2);
```
<div align="center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/117f1545-2add-450d-910d-a2f9cdc37a58">
</div>

  - 병합 할당 연산자들
```js
let x = 0;
let y = '';
let z = null;

x ||= 100;
y &&= '있어야 바뀜';
z ??= '기본값';

console.log(x, y, z);
```
<div align="center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/dd0e2b2d-9b81-4b44-83be-9076775b260d">
</div>

-----
### 연산자 우선순위
-----
  - 전체 연산자 우선순위 : ```https://developer.mozilla.org/ko/docs/Web/JavaScript/Guide/Expressions_and_Operators#%EC%97%B0%EC%82%B0%EC%9E%90_%EC%9A%B0%EC%84%A0%EC%88%9C%EC%9C%84```
<div align="center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/5c7bbce2-3be3-47fd-9ae9-b442157b6847">
</div>

```js
let x = 1;
let y = 19 === 3 + 4 * 2 ** ++x;

console.log(y);
```
<div align="center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/e6b34d9d-6a63-4f8c-b3f1-245ea5ad038c">
</div>

```js
console.log(
  2 > 3 || 4 % 2 === 0,
  2 > (3 || 4) % 2 === 0,
  2 > 3 || 4 % (2 === 0)
);
```
<div align="center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/69034ba7-68c9-4f97-8c7f-ebcf582d3267">
</div>

