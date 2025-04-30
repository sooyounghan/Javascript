-----
### Symbol
-----
1. 다른 값과 절대 중복되지 않는 유일무이한 값
   - 원시 타입
   - https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Symbol

2. 기본 생성과 활용
```js
const mySymbol = Symbol();

console.log(typeof mySymbol, mySymbol);
```
<div align="center">
<img src="https://github.com/sooyounghan/JavaScript/assets/34672301/e3f5ef83-168b-4180-89b2-fc133a326650">
</div>

```js
// 💡 new를 사용하지 않음
const mySmbol = new Symbol(); // ⚠️ 오류 발생!
```
<div align="center">
<img src="https://github.com/sooyounghan/JavaScript/assets/34672301/a1de3e33-93e2-4bb9-83f5-7a3a868f6b7c">
</div>

  - 문자열 값을 인자로 줄 수 있음
  - 해당 심벌에 대한 설명일 뿐, 각 심벌의 값은 유일 무이
```js
const symbol1 = Symbol('hello');
const symbol2 = Symbol('hello');

console.log(symbol1, symbol2);
```
<div align="center">
<img src="https://github.com/sooyounghan/JavaScript/assets/34672301/3bbb1f46-3a7c-4761-8fde-4e0f9ac66253">
</div>

  - 래퍼 객체(Symbol)의 인스턴스 프로퍼티 (즉 symobl 자체는 원시값)
```js
// 래퍼 객체(Symbol)의 인스턴스 프로퍼티
console.log(symbol1.description, symbol2.description);
```
<div align="center">
<img src="https://github.com/sooyounghan/JavaScript/assets/34672301/3e029968-d7f6-4ebb-ba04-5e69bb2a311a">
</div>

  - 래퍼 객체(Symbol)의 인스턴스 메서드
```js
// 래퍼 객체(Symbol)의 인스턴스 메서드
console.log(symbol1.toString(), symbol2.toString());
```
<div align="center">
<img src="https://github.com/sooyounghan/JavaScript/assets/34672301/f35f502c-1cd4-4d48-9da9-19727d0990e7">
</div>

  - 두 심볼은 같지 않음
```js
// ⭐️ 두 심볼은 같지 않다!
console.log(symbol1 === symbol2);
```
<div align="center">
<img src="https://github.com/sooyounghan/JavaScript/assets/34672301/f2bc10f5-e977-47f2-9b63-3f2709d7857c">
</div>

3. 객체에서의 활용 (외부적으로 키 값을 사용한 접근이 일부 허용된 객체에서 특정 프로퍼티를 감추는 용도로 사용)
   - 객체의 키로 사용 시 : [ , ]로 감쌈
```js
const obj = {
  [Symbol('x')]: 1,
  [Symbol('y')]: 2
}

console.log(obj);
```
<div align="center">
<img src="https://github.com/sooyounghan/JavaScript/assets/34672301/03b16ad7-3fc1-4dee-8cd0-3739a578df12">
</div>

  - 유일무이한 값으로 다음과 같이 출력 불가 (위의  [Symbol('x')]과  아래의  [Symbol('x')]은 유일무이한 것으로 다른 것)
```js
// 유일무이한 값이므로 다음과 같이 출력 불가
console.log(
  obj[Symbol('x')],
  obj[Symbol('y')]
);
```
<div align="center">
<img src="https://github.com/sooyounghan/JavaScript/assets/34672301/ec61905b-4f52-4c8f-b2b7-1f156f743927">
</div>

4. 외부 접근을 제한할 프로퍼티의 키로 활용
```js
const buildingKey = Symbol('secret');

const building = {
  name: '얄코사옥',
  floors: 3,
  [buildingKey]: '1234#'
}

console.log(building);

console.log(
  building.name,
  building.floors,
  building[buildingKey]
);
```
  - 즉 Symbol('secret')이라는 Symbol 객체를 buildingkey라는 상수에 저장하였고, 이를 통해 접근
<div align="center">
<img src="https://github.com/sooyounghan/JavaScript/assets/34672301/196ff255-dccd-4ccd-abc9-8c3568e7eeaf">
<img src="https://github.com/sooyounghan/JavaScript/assets/34672301/53de47f1-51c1-496a-a60f-0124f3c98b79">
</div>

  - 외부로부터의 접근 차단
```js
// 외부로부터의 접근 차단
console.log(
  building[Symbol('secret')]
);
```
<div align="center">
<img src="https://github.com/sooyounghan/JavaScript/assets/34672301/6ead62dd-7c40-4894-a693-2394cdb940c1">
</div>

  - 아래의 방법들로는 접근되지 않음
```js
for (key in building) {
  console.log(key);
}
```
<div align="center">
<img src="https://github.com/sooyounghan/JavaScript/assets/34672301/a814b88b-5217-4866-8c99-e10386f0ef57">
</div>

```js
console.log(
  Object.keys(building),
  Object.values(building),
  Object.entries(building),
  Object.getOwnPropertyNames(building)
);
```
<div align="center">
<img src="https://github.com/sooyounghan/JavaScript/assets/34672301/4897348d-8b2a-45cc-b5cd-9f65ab995e07">
</div>

  - 아래의 Object 정적 메서드로 접근 가능 (배열로 반환)
  - Obejct.getOwnPropertySymbols(object)[index] : 배열 방식 접근 가능
```js
console.log(
  Object.getOwnPropertySymbols(building),
  Object.getOwnPropertySymbols(building)[0],
);

console.log(
  building[
    Object.getOwnPropertySymbols(building)[0]
  ]
);
```
<div align="center">
<img src="https://github.com/sooyounghan/JavaScript/assets/34672301/8d7fa1e3-38e5-4602-bba6-8b626415ddf7">
</div>

-----
### 전역 심볼 레지스토리 (Global Symbol Registry)
-----
1. 키가 중복되지 않는 심볼들이 저장되는 공간 (즉, 프로그램 전체에 공유되는, 키가 중복되지 않는 심볼들이 저장되는 공간)
2. Symbol의 정적 메서드들
   - for : 주어진 인자로 전역 심볼 레지스트리에 하나의 심볼 생성 및 제한
     + 전역 심볼 레지스트리에 해당 키로 등록된 키가 없을 시 : 심볼 새로 생성
     + 전역 심볼 레지스트리에 해당 키가 존재할 시 : 해당 심볼 반환
```js
// 전역 심볼 레지스트리에 해당 키로 등록된 키가 없을 시:
// 심볼을 새로 생성
const symbol1 = Symbol.for('hello');

// 전역 심볼 레지스트리에 해당 키가 존재할 시:
// 해당 심볼을 반환
const symbol2 = Symbol.for('hello');

console.log(symbol1 === symbol2);
```
<div align="center">
<img src="https://github.com/sooyounghan/JavaScript/assets/34672301/be237ef6-9019-4f0c-8549-7d6895d571c2">
</div>

```js
const obj = {
  [symbol1]: 'SECRET STRING'
}

console.log(
  obj[Symbol.for('hello')] // obj[symbol1]
);
```
<div align="center">
<img src="https://github.com/sooyounghan/JavaScript/assets/34672301/53620ead-5cd0-472a-bdaf-e3809ff2e0ed">
</div>

  - for 메서드로 생성되지 않은 심볼과는 다름 (전역 심볼 레지스트리에 저장되지 않음)
```js
// ⚠️ for 메서드로 생성되지 않은 심볼과는 다름
const symbol3 = Symbol('hello'); // 전역 심볼 레지스트리에 저장 ❌

console.log(symbol1 === symbol3);
```
<div align="center">
<img src="https://github.com/sooyounghan/JavaScript/assets/34672301/6acbc877-834f-48ef-bcd0-8ef80a0a8791">
</div>

  - keyFor : 정적 심볼 레지스트리에 저장된 심볼의 키 반환
```js
console.log(
  Symbol.keyFor(symbol1),
  Symbol.keyFor(symbol2)
);
```
<div align="center">
<img src="https://github.com/sooyounghan/JavaScript/assets/34672301/f254dda3-e8bf-4d36-8fd0-c2b4d36de219">
</div>

  - 전역 심볼 레지스트리에 저장되지 않은 심볼에는 작동하지 않음
```js
// ⚠️ 전역 심볼 레지스트리에 저장되지 않은 심볼에는 작동하지 않음
console.log(
  Symbol.keyFor(symbol3)
);
```
<div align="center">
<img src="https://github.com/sooyounghan/JavaScript/assets/34672301/6ee6e8c9-0061-4abc-8a3c-8191e8e180b7">
</div>

-----
### 전역 심볼 레지스토리 (Global Symbol Registry)의 심볼 (Symbol)
-----
```js
// 숫자 요소들의 평균을 구하는 메서드 추가
Array.prototype[Symbol.for('average')] = function () {
  let sum = 0, count = 0;
  for (const i of this) {
    if (typeof i !== 'number') continue;
    count++;
    sum += i;
  }
  return sum/count
}

[1, 2, 3, 4, 5, 6][Symbol.for('average')]();
```
<div align="center">
<img src="https://github.com/sooyounghan/JavaScript/assets/34672301/e08604e3-4b1c-471d-b35b-816ce86fabd7">
</div>

: 표준 빌트인 객체에 직접 만든 메서드를 만들어 넣을 경우 이후 버전의 자바스크립트에서 같은 이름의 메서드가 추가되더라도, 커스텀 메서드가 덮어씌워지지 않도록 하기 위한 용도로 사용 가능
