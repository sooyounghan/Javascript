-----
### 객체 생성과 프로퍼티 접근
-----
1. 일반적인 객체 생성
```js
const food1 = {
  name : '햄버거',
  price : 5000,
  vegan : false
};

console.log(food1);
```
<div align="center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/306f2f0a-68f0-4184-aef4-3a64ae2101e4">
</div>

2. 일반적인 객체 프로퍼티 접근
```js
console.log(
  food1.name, // 마침표 프로퍼티 접근 연산자
  food1['price'] // 대괄호 프로퍼티 접근 연산자
);
````
<div align="center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/f22a06b6-0583-4035-abe1-8045b85a34d9">
</div>

3. 빈 객체 생성
```js
const food2 = {};
console.log(food2);
```
<div align="center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/63a8b6bb-5a5f-4a49-85a5-1233cf0dcd9c">
</div>

4. 프로퍼티 추가
```js
// 프로퍼티 추가
food2.name = '샐러드';
food2.price = '6000';
food2['vegan'] = true;

console.log(food2);
```
<div align="center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/d3b27bf0-1e8c-4a2b-bf2d-b41d6bfc85d5">
</div>

5. 프로퍼티 수정
```js
// 프로퍼티 수정
food2['price'] = '6500';
food2.vegan = false;

console.log(food2);
```
<div align="center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/b9e83089-d2d3-4f38-936a-5333722a2d56">
</div>

5. 식별자 명명 규칙에 벗어나는 키 이름 사용 시
   - 변수명 등으로 사용할 수 없는 이름의 키인 경우 (예) 숫자로 시작, - 삽입, 공백 추가)
   - 식별자 명명 규칙 : https://developer.mozilla.org/ko/docs/Glossary/Identifier

```js
const obj = {
  1 : '하나', // 숫자도 객체의 키로 사용 가능
  'ab-cd' : 'ABCD', // 문자 포함 시 키도 따옴표로 감싸야 함
  's p a c e' : 'Space'
}

// 대괄호 프로퍼티 접근 연산자로만 가능
console.log(
  obj[1],
  obj['ab-cd'],
  obj['s p a c e']
);

/* 오류 발생
console.log(
  obj.1
  obj.ab-cd
  obj.s p a c e
);
*/
```
<div align="center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/c5cc0b40-c94d-4d79-a7bd-e6a5e5113ee4">
<img src="https://github.com/sooyounghan/Web/assets/34672301/79dcdac9-b052-47a0-b8b4-78778431d6dd">
<img src="https://github.com/sooyounghan/Web/assets/34672301/1ed572b7-ec73-42d4-ad2e-06f2f62a2b66">
</div>

-----
### 표현식으로 키 값 정의하기
-----
1. 대괄호 [] 사용
```js
let idx = 0;
const obj = {
  ['key-' + ++idx] : `value-${idx}`,
  ['key-' + ++idx] : `value-${idx}`,
  ['key-' + ++idx] : `value-${idx}`,
  [idx ** idx] : 'POWER'
}

console.log(obj);
```
<div align="center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/8c5c8aba-f326-42dd-b008-3085410191dc">
</div>

2. 객체나 배열을 키 값으로 사용 시
```js
const objKey = { x : 1, y : 2};
const arrKey = [1, 2, 3];

const obj = {
  [objKey] : '객체를 키값으로',
  [arrKey] : '배열을 키값으로'
}
```

```js
console.log(
  obj[objKey],
  obj[arrKey]
);
```
  - 즉, 객체 { a: 1, b: 2 }는 객체로 키 값이 저장되는 것이 아니라, 객체 자체를 '[object Object]'라는 String으로 저장
  - 마찬가지로, [1, 2, 3]는 배열로 저장되는 것이 아니라, 배열 자체를 ['1,2,3']이라는 String으로 저장
<div align="center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/aab1d437-eb59-4562-b0e6-cf0bd88a28f9">
</div>

```js
// ⚠️ ???????
console.log(
  obj[{ a: 1, b: 2, c: 3 }], // 내용이 다른 객체
  obj['1,2,3'] // 문자열
);

// Log를 펼쳐 키 값 확인 : 문자열
// 객체와 배열이 그 자체가 아니라 문자열로 치환되어 키가 되는 것
console.log(obj);
```
  - [objKey] : [object Object]라는 String으로 저장
  - 즉, 객체 { a: 1, b: 2, c: 3 }는 객체로 키 값이 저장되는 것이 아니라, 객체 자체를 '[object Object]'라는 String으로 저장 : 따라서, 동일하게 출력
  - 마찬가지로, ['1,2,3']는 배열로 저장되는 것이 아니라, 배열 자체를 String으로 저장 : 따라서, 동일하게 출력
<div align="center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/984b05bb-d66b-49d4-a60d-55c4d287aaaf">
<img src="https://github.com/sooyounghan/Web/assets/34672301/7bc46fdb-794f-4044-b476-cbe6a15d4038">
<img src="https://github.com/sooyounghan/Web/assets/34672301/2913cf4d-087e-4a01-a595-1a653e430043">
</div>

```js
console.log(
  obj['[object Object]']
);
```
  - 즉, 실제로 해당 객체나 배열의 내용이나 참조값이 키가 되는 것이 아니라 문자열로 치환되어 저장
    + 객체 : 무엇이던 간에 '[object Object]'라는 문자열로 치환
    + 배열 : ['배열 요소']로 치환
  - Map(참조값을 키값으로 사용)과의 차이점
<div align="center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/59cbaee8-806d-4c99-b61e-2475eba12fe2">
</div>

-----
### 프로퍼티 삭제 (delete 연산자)
-----
```js
const person1 = {
  name: '홍길동',
  age: 24,
  school: '한국대',
  major: '컴퓨터공학'
};

console.log(person1);
```

```js
delete person1.age;
console.log(person1);
```

```js
delete person1['major'];
console.log(person1);
```

```js
delete person1.hobby;
console.log(person1);
```
  : 오류가 발생하지는 않음
  
<div align="center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/a5ed6c7e-4d7d-4977-bb57-8e3a512cbbc0">
</div>

-----
### 키의 동적 사용
-----
  - 동적으로 사용할 때는, 콤마 연산자가 아닌 대괄호 연산자로 사용
  - 콤마 연산자로 하면, key라는 키 값을 넣는 것으로 인식
```js
const product1 = {
  name : '노트북',
  color : 'gray',
  price : 800000
}

function addModifyProperty (obj, key, value) {
  // obj.key = value; // 의도와 다른 작업 수행 (obj 객체의 key라는 이름의 키의 값에 접근하겠다는 뜻)
  obj[key] = value;
}

function deleteProperty (obj, key) {
  // delete obj.key; // 의도와 다른 작업 수행 (obj 객체의 key라는 이름의 키의 값에 접근하겠다는 뜻)
  delete obj[key];
}
```

```js
addModifyProperty(product1, 'inch', 16);
console.log(product1);
```

```js
addModifyProperty (product1, 'price', 750000);
console.log(product1);
```

```js
deleteProperty(product1, 'color');
console.log(product1);
```
<div align="center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/ae6ddfc1-71a1-4d81-b900-dea11127825b">
</div>

-----
### ES6 추가 문법
-----
1. 객체 선언 시, 프로퍼티 키와 대입할 상수 / 변수명이 동일할 시 단축 표현
```js
const x = 1, y = 2;

const obj1 = {
  x : x,
  y : y
}

console.log(obj1);
```
  - obj1 객체에 x, y라는 key
  - 위에서 언급한 x = 1, y = 2를 value로 삽입 (식별자와 같은 이름이면 단축 가능)
<div align="center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/c77e6a06-8581-4d77-a614-7c93361c5a92">
</div>

```js
const obj2 = { x, y }

console.log(obj2);
```
<div align="center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/e63ba7a6-eea2-4ece-bdf5-c27664dc2a8b">
</div>

```js
function createProduct(name, price, quantity) {
  return { name, price, quantity };
}

const product1 = createProduct('선풍기', 50000, 50);
const product2 = createProduct('청소기', 125000, 32);

console.log(product1, product2);
```
<div align="center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/3f7ed8b1-0696-47a2-9a37-ad30a22f95f0">
</div>

2. 메서드(Method) : 객체에 축약표현으로 정의된 함수 프로퍼티
```js
// 일반 함수 프로퍼티 정의
const person = {
  name : '홍길동',

  salutate : function (formal) {
    return formal
    ? `안녕하십니까, ${this.name}입니다.`
    : `안녕하세요. ${this.name}이에요.`;
  }
}
console.log(person.salutate(true));
```
<div align="center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/5fc594c0-9340-4f13-9d6a-d7079b729af0">
</div>

```js
// 메서드 정의
const person = {
  name : '홍길동',

  salutate (formal) {
    return formal
    ? `안녕하십니까, ${this.name}입니다.`
    : `안녕하세요. ${this.name}이에요.`;
  }
}
console.log(person.salutate(true));
```
<div align="center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/3e733541-d943-4ea1-b628-e9fe24b0dba8">
</div>

  - ES6에서부터는 위의 표현으로 정의된 함수만 메서드라고 부름
  - 일반 함수 프로퍼티와 특성이 다름
