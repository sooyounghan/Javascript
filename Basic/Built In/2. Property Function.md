-----
### 빌트인 전역 프로퍼티 (Built-In Global Property)
-----
: https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects#%ED%95%AD%EB%AA%A9%EB%B3%84_%ED%91%9C%EC%A4%80_%EA%B0%9D%EC%B2%B4
1. 스스로 다른 프로퍼티나 메서드를 갖지 않고 값만 반환
```js
console.log(globalThis.Infinity);
console.log(globalThis.NaN);
console.log(globalThis.undefined);

console.log(globalThis.globalThis);
```
<div align="center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/bb7e0da9-6388-4d88-a42a-e0ca085fd082">
<img src="https://github.com/sooyounghan/Web/assets/34672301/3fce77bf-b4ca-4088-934f-3b5889829074">
<img src="https://github.com/sooyounghan/Web/assets/34672301/13aef21d-bd08-46c4-af3f-0396d5d8f2b2">
</div>

```js
console.log(
  globalThis == globalThis.globalThis,
  globalThis == globalThis.globalThis.globalThis,
  globalThis == globalThis.globalThis.globalThis.globalThis
);
```
<div align="center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/52bd535c-d059-445b-88ae-d04a324a29da">
</div>

2. Infinity, NaN, undefined 등의 원시값들은 global.Infinity, global.NaN, global.undefined를 가리킴
3. null은 가리키는 값이 없음을 의미하므로 포함되지 않음
4. globalThis : 스스로에 대한 참조를 프로퍼티로 포함

-----
### 빌트인 전역 함수 (Built-In Global Function)
-----
: https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects#%ED%95%A8%EC%88%98_%EC%86%8D%EC%84%B1
1. eval
   - 문자열로 된 코드를 받아 실행
   - 값을 반환하는 코드 (표현식) 이라면, 해당 값을 반환
```js
const x = eval('1 + 2 + 3');

// 객체나 함수의 리터럴은 괄호로 감싸야 함
const obj = eval('({a : 1, b : 2})');

console.log(x, obj);
```
<div align="center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/baa89fd6-f9e7-40df-8aee-801a99d7303f">
</div>

  - 표현식이 아닐 경우 해당 코드 실행
```js
const code = `
  let x = 1;
  console.log(x++, x);
`;

eval(code);
```
<div align="center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/e8547727-7744-4aad-b425-0536a5970f78">
</div>

  - 매우 특별한 경우가 아닌 이상 절대 사용하지 말것
  - 보안에 취약함
  - 엔진이 코드를 최적화 하지 못하므로 처리 속도가 느림
  - 관련 문서 : https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/eval#eval%EC%9D%84_%EC%A0%88%EB%8C%80_%EC%82%AC%EC%9A%A9%ED%95%98%EC%A7%80_%EB%A7%90_%EA%B2%83!
  
2. isFinite
   - 유한수 여부 반환
```js
console.log(
  isFinite(1),
  isFinite(0),
  isFinite('1'),
  isFinite(null)
);
```
<div align="center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/cc2ece5f-19cb-400e-b663-66a5dd0d2df1">
</div>

  - 유한수이거나 유한수로 평가될 수 있는 값 (null은 0) : true

```js
console.log(
  isFinite(1/0),
  isFinite(Infinity),
  isFinite(-Infinity),
  isFinite(NaN),
  isFinite('abc')
);
```
<div align="center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/2e509d84-aa0d-4374-9c65-0b1cf705007d">
</div>

  - 무한수이거나 수로 평가될 수 없는 값 : false

3. isNaN
   - NaN 여부 반환
```js
console.log(
  isNaN(NaN),
  isNaN('abcde'),
  isNaN({}),
  isNaN(undefined)
);
```
<div align="center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/ca41d2d9-7e80-4bc4-8f56-2277d1ab7cb9">
</div>

  - 숫자로 인식될 수 없는 값 : true
  - Number 타입이 아닌 경우 Number로 변환하여 평가 (NaN도 타입은 Number)
  - Number.isNaN은 타입 변환을 하지 않음

4. parseFloat
   - 인자로 받은 값을 실수로 변환
```js
console.log(
  parseFloat(123.4567),
  parseFloat('123.4567'),
  parseFloat(' 123.4567 ')
);
```
<div align="center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/d71eec00-edb8-435d-aeec-8471412d832d">
</div>

  - 문자열의 겨우, 앞/뒤 공백은 무시
```js
console.log(
  parseFloat('123.0'),
  parseFloat('123'),
  parseFloat(' 123ABC '),
  parseFloat([123, 456, 789])
);
```
<div align="center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/6dbc1e63-fe01-47aa-9fb3-c2c1f8959d2c">
</div>

  - 숫자로 시작할 경우 읽을 수 있는 부분까지 숫자로 변환
  - 배열의 경우 첫 요소가 숫자면 해당 숫자 반환

```js
console.log(
  parseFloat('ABC123'),
  parseFloat({x: 1}),
  parseFloat([]),
  parseFloat(['a', 1, true])
);
```
<div align="center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/c9845145-176d-42f3-80ee-1b7c90f92cb3">
</div>

  - 기타 숫자로 변환이 안 되는 경우 NaN 반환

5. parseInt
   - 인자로 받은 값을 정수 (타입은 실수)로 변환
```js
console.log(
  parseInt(123),
  parseInt('123'),
  parseInt(' 123.4567 '),
  parseInt('345.6789')
);
```
<div align="center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/df2c871a-4eb6-4a02-b3f9-e237514c2a2f">
</div>

  - 소수점 뒤 숫자는 버림 (반올림하지 않음)

```js
console.log(
  parseInt('abc'),
  parseInt('{}'),
  parseInt('[]')
);
```
<div align="center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/c6379f61-8ef2-48bc-8cab-f79e06614a6b">
</div>

  - 두 번째로 인자로 숫자(2-36)를 넣으면 ?
```js
console.log(
  parseInt('11'),
  parseInt('11', 2),
  parseInt('11', 8),
  parseInt('11', 16),
  parseInt('11', 32),

  parseInt('11', 37),
  parseInt('11', 'A'),
);
```
<div align="center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/f758828e-e607-4456-8caf-5d661ac2cddd">
</div>

  - 주어진 값을 해당 진법의 숫자로 해석하여 10진법 숫자로 반환
  - 무효한 숫자는 NaN 반환, 엉뚱한 값은 해당 숫자를 반환

6. encodeURI, encodeURIComponent
```js
const searchURI = 'https://www.google.com/search?q=얄코';
const encodedURI = encodeURI(searchURI);

console.log(encodedURI);
```
<div align="center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/0455223e-cc50-4bf1-8f45-3322c3f0b815">
</div>

  - URI(인터넷 자원 주소)는 아스키 문자 Set으로만 구성되어야 함
  - 아스키가 아닌 문자(한글 등)와 일부 특수문자를 포함한 URI를 유효하게 인코딩

```js
const keyword = '얄코';
const encodedKeyword = encodeURIComponent(keyword);

console.log(encodedKeyword);

const searchURI = `https://www.google.com/search?q=${encodedKeyword}`;
console.log(searchURI);
```
<div align="center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/345cf1c7-ad9a-4d06-9575-9c3b1e2ecaf5">
</div>

  - 둘의 정확한 차이
```js
const raw = '?q=얄코';
console.log(encodeURI(raw));
console.log(encodeURIComponent(raw));
```
<div align="center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/b9997b22-d66a-4fc5-86ea-77783a1e02d8">
</div>

  - URI에서 특정 기능을 갖는 =, ?, & 등을 인코딩하는가 여부
  - encodeURI : 인자를 완성된 URI 요소로 인식 (즉, ?q=인자, 이 인자를 URI로 인식) [전체 URI]
  - encodURIComponent : 인자를 완성된 요소로 인식 (즉, ?q=인자 전체를 URI로 인식) [특정 키워드만]

7. decodeURI, decodeURIComponent
   - encodeURI(Component) 와 반대로 동작
```js
const encodedURI = 'https://www.google.com/search?q=%EC%96%84%EC%BD%94';
const decodedURI = decodeURI(encodedURI);

console.log(decodedURI);

const encodedComp = '%EC%96%84%EC%BD%94';
const decodedComp = decodeURI(encodedComp);

console.log(decodedComp);
```
<div align="center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/3b6f3299-3acc-4b16-9c68-5c09bca83981">
</div>
