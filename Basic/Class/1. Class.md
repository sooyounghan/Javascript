-----
### 클래스 (Class)
-----
1. 객체를 생성하기 위한 Template
2. https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Classes
3. 클래스(Class)를 사용하여 인스턴스 생성
```js
class YalcoChicken {
  constructor (name, no) {
    this.name = name;
    this.no = no;
  }
  introduce () { // 메서드(Method)
    return `안녕하세요, ${this.no}호 ${this.name}점 입니다.!`;
  }
}

const chain1 = new YalcoChicken('판교', 3);
const chain2 = new YalcoChicken('강남', 17);
const chain3 = new YalcoChicken('제주', 24);

console.log(chain1, chain1.introduce());
console.log(chain2, chain2.introduce());
console.log(chain3, chain3.introduce());
```
<div align="center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/2727fd7e-6127-4c6a-8dfc-bf5e43e77a42">
</div>

-----
### Syntatic Sugar
-----
1. 즉, 클래스를 프로토타입의 Syntatic Sugar라고 부르기도 함
2. 자바 등 타 언어에 익숙한 사람들을 위해 생성자 함수, 프로토타입 기반 자바스크립트 문법을 타 언어의 클래스와 비슷한 문법으로 포장
3. 즉, 문법을 보다 읽기 쉽게 만드는 것
4. 그러나 클래스와 생성자 함수의 동작이 동일하지 않음
  - 클래스는 Hoisting 되지 않음 (정확히는 되는 것이 맞음)

```js
const chain1 = new YalcoChicken('판교', 3);

class YalcoChicken {
  constructor (name, no) {
    this.name = name;
    this.no = no;
  }
  introduce () {
    return `안녕하세요, ${this.no}호 ${this.name}점 입니다!`;
  }
}
```
<div align="center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/0b7f6a98-e11d-4e49-945e-e0ca9e7c3a1b">
</div>

  - 클래스는 new 없이 사용하면 오류 (생성자 함수는 오류 없이 undefined 반환)
```js
const chain2 = YalcoChicken('강남', 17);
```
<div align="center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/d873957e-f247-4e13-b2e2-1d63073bc83e">
</div>

-----
### Constructor Method
-----
1. 클래스의 인스턴스 객체를 생성하고 초기화하는 메서드 (하나만 선언 가능)
2. https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Classes/constructor
3. 인스턴스 생성시 인자를 받아 프로퍼티를 초기화
4. 다른 메서드 이름을 쓸 수 없음 (즉, constructor 로만 가능)
5. 기본값 사용 가능 (married = false)
6. 필요 없을 시(인자가 없을 때) 생략 가능
7. 값을 반환하지 말 것 (생성자 함수처럼 암묵적 this 반환)
```js
class Person {
  constructor (name, age, married = false) {
    this.name = name;
    this.age = age;
    this.married = married;
  }
}

const person1 = new Person('박영희', 30, true);
const person2 = new Person('오동수', 18);
console.log(person1, person2);
```
<div align="center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/9f1c8bb4-1d97-414a-ba3a-3b3f7a2b0e20">
</div>

```js
// 인스턴스 초기화가 필요 없는 클래스
class Empty { }
console.log(new Empty());
```
<div align="center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/817e6787-a4c3-4788-87bc-ba00c614d28b">
</div>

-----
### Class의 Method
-----
```js
class Dog {
  bark() {
    return '멍멍';
  }
}

const badugi = new Dog();
console.log(badugi, badugi.bark());
```
<div align="center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/5ac3cc4f-08e9-4535-886c-b2b01085551d">
</div>

  - Dog Class에 선언한 bark() 메서드는 Prototype에 존재
  - 생성자 함수나 객체가 ProtoType으로 가지고 있는 속성이나 메서드는 instance에서 사용 가능하긴 하나, Prototype에서 가지고 있음
  - 생성자 함수에 넣은 함수의 차이 : 클래스는 프로토타입에서 생성
    
```js
function Dog2() {
  this.bark = function() {
    return '멍멍';
  }
}

const badugi = new Dog2();
console.log(badugi, badugi.bark());
```
<div align="center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/8dd5cb39-14bb-4cde-bb81-1dd893dc8611">
</div>

  - 생성자 함수의 속성은 해당 객체 내에서 생성
    
-----
### 필드 (Field)
-----
1. constructor 밖, 즉 this.~ 없이 인스턴스의 프로퍼티 정의
2. 이미 다수 브라우저에서 지원
3. 이후 Babel로 해결 가능
4. https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Classes/Public_class_fields

```js
class Slime {
  hp = 50;
  op = 4;
  attack (enemy) {
    enemy.hp -= this.op;
    this.hp += this.op/4;
  }
}

const slime1 = new Slime();
const slime2 = new Slime();

console.log(slime1, slime2);
```
<div align="center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/b85ba7f4-d93f-4be8-aee7-02e4dacd3fd3">
<img src="https://github.com/sooyounghan/Web/assets/34672301/d970185d-728d-4dc7-a05a-be8c82b73276">
</div>

```js
slime1.attack(slime2);

console.log(slime1, slime2);
```
<div align="center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/32e5d7d6-5004-429a-b92b-537d964bf5cd">
</div>

```js
class YalcoChicken {
  no = 0;
  menu = { '후라이드' : 10000, '양념치킨' : 12000 };

  constructor (name, no) {
    this.name = name;
    if(no) this.no = no;
  }

  introduce() {
    return `안녕하세요. ${this.no}호 ${this.name} 점 입니다!`;
  }

  order (name) {
    return `${this.menu[name]}원 입니다.`;
  }
}

const chain0 = new YalcoChicken('(미정)');
console.log(chain0, chain0.introduce());
```
<div align="center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/b8512635-f35d-4e14-9907-652f199b471f">
</div>

```js
const chain1 = new YalcoChicken('판교', 3);
console.log(chain1, chain1.introduce());
```
<div align="center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/e57d402d-f762-4113-8b78-102f118d38cb">
</div>

```js
chain1.menu['양념치킨'] = 13000;

console.log(chain0.order('양념치킨'), chain1.order('양념치킨'));
```
<div align="center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/f8687915-1967-47ac-93c2-21c2c706ff4f">
</div>

-----
### 정적(Static) 필드(Field)와 메서드(Method)
-----
1. https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Classes/static
```js
class YalcoChicken {
  // 정적 필드와 메서드
  static brand = '얄코치킨';
  static contact() {
    return `${this.brand}입니다. 무엇을 도와드릴까요?`;
  }

  constructor (name, no) {
    this.name = name;
    this.no = no;
  }

  introduce () {
    return `안녕하세요. ${this.no}호 ${this.name} 점 입니다!`;
  }
}

console.log(YalcoChicken);
console.log(YalcoChicken.contact());
```

  - introduce 함수는 Method이므로 Prototype의 한 영역에 존재
<div align="center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/92d5ac63-6adb-4714-8ca3-f7a0d13f9116">
</div>

<div align="center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/6fb03b7d-bad3-4973-acff-38b3110b47c3">
</div>


1. 인스턴스 수와 관계없이 메모리 한 곳만 차지
2. 인스턴스 없이 클래스 차원에서 호출
3. 정적 메서드에서는 정적 필드만 사용 가능 (즉, static 메서드는 static filed만 호출 가능)
   - static 메서드에서 instance 필드 접근 불가

-----
### 클래스 (Class) = 함수 (Function)
-----
```js
class Dog {
  bark() {
    return '멍멍';
  }
}

console.log(typeof Dog);

const 개 = Dog; // 함수 : 할당될 수 있는 일급 객체
const 바둑이 = new 개();

console.log(바둑이);
```
<div align="center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/7736373d-54e9-43e2-8699-ea0a734d86f1">
</div>

1. typeof시 function으로 구분
2. 클래스는 일급 객체로, 다른 곳에 할당 가능

