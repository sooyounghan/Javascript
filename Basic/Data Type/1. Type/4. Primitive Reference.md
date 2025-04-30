-----
### 값 복사 결과 비교
-----
1. 원시 타입 (Primitive Type) : https://developer.mozilla.org/ko/docs/Glossary/Primitive
   - string, number, bigint, boolean, undefined, symbol, null
   - 값에 의한 복사 (Copy of value)
```js
let number1 = 1;
let string1 = 'ABC';
let bool1 = true;

let number2 = number1;
let string2 = string1;
let bool2 = bool1;

number2 = 2;
string2 = '가나다';
bool2 = false;

console.log('~1:', number1, string1, bool1);
console.log('~2:', number2, string2, bool2);
```
<div align="center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/ab433769-593e-44f8-8fee-785171264748">
</div>

<div align="center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/c97ac2a1-a95e-420d-980a-054f419c6ed3">
</div>


2. 참조 타입 : 참조에 의한 복사 (Copy of refenece)
```js
const obj1 = {
  num : 1,
  str : 'ABC',
  bool : true
};

const obj2 = obj1;
// obj2 = { }; // 오류

console.log('obj1 : ', obj1);
console.log('obj2 : ', obj2);

// const임에도 내부 값은 변경 가능함
// 내부 변경 방지는 Object.freeze 함수로 가능
obj2.num = 2;
obj2.str = '가나다';
obj2.bool = false;

console.log('obj1 : ', obj1);
console.log('obj2 : ', obj2);
```
<div align="center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/ad5f5e87-a56d-4dad-ab71-213be9602ee5">
</div>

```js
const array1 = [1, 'ABC', true];
const array2 = array1;
// array2[] = []; // 오류

console.log('array1 : ', array1);
console.log('array2 : ', array2);

// const임에도 내부 변경 값은 변경 가능함 주목
array2[0] = 3;
array2[1] = 'def';
array2[2] = false;

console.log('array1 : ', array1);
console.log('array2 : ', array2);
```

<div align="center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/e49fc268-2618-4046-a1e7-e75175bdf389">
</div>

<div align="center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/11165fb7-9356-4e65-83cd-ed92598004ac">
</div>

-----
### 메모리 상세
-----
1. 원시 타입
```js
let number1 = 1;
number2 = number1;
number2 = 2;

console.log(number1, number2);
```
<div align="center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/e97a6e5f-4dde-4dd2-9326-f7502af8bb50">
</div>

<div align="center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/05e1b8f1-bf0d-4499-8730-f3ded2ca2bb7">
<img src="https://github.com/sooyounghan/Web/assets/34672301/e1cb778b-8f0d-4485-bd9b-d01dcb9c93ad">
<img src="https://github.com/sooyounghan/Web/assets/34672301/ea7b6c8c-fca4-4e1d-b3c5-a08e1646a2ac">
</div>

```js
const obj1 = {
  num : 1,
  str : 'ABC',
  bool : true
};

const obj2 = obj1;

obj2.num = 2;

console.log(obj1, obj2);
```

<div align="center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/bbb1529d-c62b-4321-9b10-f86c2fda4eed">
</div>

<div align="center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/1274e711-56ae-4e1f-a9c7-0fa24769d2a6">
</div>

```js
const array1 = [1, 'ABC', true];
const array2 = array1;

array2[1] = '가나다';

console.log(array1, array2);
```
<div align="center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/f646059f-f917-417b-b70b-8cea379c9071">
</div>

<div align="center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/9696eecd-323d-4962-811e-94148cb20381">
</div>
