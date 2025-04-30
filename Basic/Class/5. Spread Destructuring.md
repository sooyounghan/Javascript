-----
### 스프레드 (Spread) (= 일종의 복사)
-----
1. 기본 문법
```js
const class1 = {
  x : 1,
  y : 'A',
  z : true
};

const class2 = { ...class1 }; // 프로퍼티들을 하나하나 복사해서 가져옴

// 참조 복사 코드와 다름
// const class2 = class1; (같은 주소를 가리키는 것)

console.log(class2);
```
<div align="center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/55db8b78-dd4c-49c6-83f2-0636343278d5">
</div>

2. 특정 객체의 프로퍼티를 포함하는 다른 객체 생성에 유용
```js
const class1 = {
  a : 1,
  b : 'A',
  c : true
};

const class2 = {
  d : { x : 10, y : 100 },
  e : [1, 2, 3]
};

const class3 = {
  ...class1,
  z : 0
};

const class4 = {
  ...class2,
  ...class3,
  ...class2.d
}

console.log(class3);

console.log(class4);
```
<div align="center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/3c88e588-c567-4be6-ae38-c06c3a4809fd">
</div>

3. 중복되는 프로퍼티는 뒤의 것이 덮어씀
```js
const class1 = {
  ...{ a : 1, b : 2},
  ...{ b : 3, c : 4, d : 5},
  ...{ c : 6, d : 7, e : 8}
}

console.log(class1);
```
<div align="center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/9f1ed731-862f-47a2-b44b-6785ce2315f8">
</div>

4. 복사의 깊이
```js
const class1 = {
  x : 1,
  y : { a : 2},
  z : [3, 4]
};

const class2 = { ...class1 };

class1.x++;
class1.y.a++;
class1.z[0]++;

console.log(class1);
console.log(class2);
```
<div align="center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/59433242-d64e-441d-88e1-183af1ce7d71">
</div>

  - 해당 객체 바로 안쪽의 원시값은 복제하지만, 참조값은 같은 값을 가리킴
  - 원시값만 있는 객체만 값에 의한 복사 (얕은 복사)
  - 복합적인 객체의 완전한 깊은 복사는 추후에 배움

-----
### 디스트럭쳐링 (Destructuring)
-----
1. 문법
```js
const obj1 = {
  x : 1,
  y : 2,
  z : 3
};

const x = obj1.x;
const y = obj1.y;
const z = obj1.z;

console.log(x, y, z);
```
<div align="center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/09aff2f1-1f5a-46ec-ae11-374f8382dca7">
</div>

  - 디스트럭쳐링으로 간략화
```js
const obj1 = {
  x : 1,
  y : 2,
  z : 3
};

const {x, y, z} = obj1;

console.log(x, y, z);
```
<div align="center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/084d096b-d7fd-4350-bfd9-a7aaee2b0ff7">
</div>

  - 일부만 가져오는 것도 가능
```js
const obj1 = {
  x : 1,
  y : 2,
  z : 3
};

const {x, z} = obj1;

console.log(x, z);
```
<div align="center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/b11462ee-09e0-452e-9d0c-8acce6761da0">
</div>

2. 활용
   - 필요한 프로퍼티 값을 짧은 코드로 변수 / 상수에 담을 때
```js
const array1 = [1, 2, 3, 4, 5];

// const length = array1.length;
const { length } = array1;

console.log(length);
```
<div align="center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/de4de812-241b-43c6-9d8b-b7cc349e1f19">
</div>

  - 함수 인자값의 가독성을 위해 객체를 사용할 때
```js
// 인자가 많은 함수는 좋지 않음
function introduce(name, age, job, married) {
  console.log(`제 이름은 ${name},`
    + `나이는 ${age}세구요.`
    + `직업은 ${job},`
    + `${married ? '기혼' : '미혼'}입니다.`
  )
}

// 여러 인자는 순서가 중요하여 가독성이 떨어짐
introduce('김철수', 28, '개발자', false);
```
<div align="center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/58d085fe-45fe-4f68-a823-2c735d892330">
</div>

```js
// 인자를 하나의 객체로 묶어 받음
function introduce(person) {
  console.log(`제 이름은 ${person.name},`
    + `나이는 ${person.age}세구요.`
    + `직업은 ${person.job},`
    + `${person.married ? '기혼' : '미혼'}입니다.`
  )
}

// 가독성이 좋음, 프로퍼티명만 제대로 입력하면 순서 무관
const person1 = {
  job : '개발자',
  age : 28,
  married : false,
  name : '김철수',
  blood : 'O' // 추가로 인자를 줘도 무관
};

introduce(person1);
```
<div align="center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/4a73ca73-3c5d-45df-ae3f-43619f2f708e">
</div>

```js
// 디스트럭쳐링
function introduce({age, married, job, name}) {
  // 순서 무관
  // 이 프로퍼티들을 갖는 객체를 인자로 받겠다는 의도
  console.log(`제 이름은 ${name},`
    + `나이는 ${age}세구요.`
    + `직업은 ${job},`
    + `${married ? '기혼' : '미혼'}입니다.`
  )
}

const person1 = {
  job : '개발자',
  age : 28,
  married : false,
  name : '김철수',
  blood : 'O' // 추가로 인자를 줘도 무관
};

introduce(person1);
```
<div align="center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/c1273bf9-6068-4d84-b9e7-38b051f605a0">
</div>
