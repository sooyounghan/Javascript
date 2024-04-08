-----
### 생성자 함수의 필요성
-----
```js
const chain1 = {
  name : '판교',
  no : 3,
  introduce() {
    return `안녕하세요, ${this.no}호 ${this.name}점입니다!`;
  }
};

const chain1 = {
  name : '판교',
  no : 17,
  introduce() {
    return `안녕하세요, ${this.no}호 ${this.name}점입니다!`;
  }
};

const chain3 = {
  name : '제주',
  no : 24,
  introduce() {
    return `안녕하세요, ${this.no}호 ${this.name}점입니다!`;
  }
};
```

- 이처럼 같은 형식의 객체들을 다수 만들어야 한다면?
```js
// 생성자 함수
function YalcoChicken(name, no) {
  this.name = name;
  this.no = no;
  this.introduce = function() {
    return `안녕하세요. ${this.no}호 ${this.name}점입니다!`;
  }
}

// 인스턴스 생성
const chain1 = new YalcoChicken('판교', 3);
const chain2 = new YalcoChicken('강남', 17);
const chain3 = new YalcoChicken('제주', 24);

console.log(chain1, chain1.introduce());
console.log(chain2, chain2.introduce());
console.log(chain3, chain3.introduce());
```
<div align="center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/79de65a7-0722-4346-a914-fdf30d3cd637">
</div>

  - chain1, chain2, chain3 모두 YalcoChicken 객체임을 알 수 있음
  - this.introduce = function ( .. )는 Method가 아님


1. 생성자 함수명 : 일반적으로 대문자로 시작 (Pascal Case)
2. 생성자 함수로 만들어진 객체 : 인스턴스 (Instance)
3. this.~로 생성될 인스턴스의 프로퍼티들 정의
4. 생성자 함수는 new 연산자와 함께 사용
5. 암묵적으로 this 반환
6. 생성자 함수에는 메서드 정의 불가 : 객체 리터럴과 클래스에서는 가능
7. new를 붙이지 않으면, undefined 반환 (즉, 호출 시 new를 붙이는가 여부에 따라 호출 원리가 다름)
```js
function YalcoChicken (name, no) {
  this.name = name;
  this.no = no;
  this.introduce = function () {
    return `안녕하세요, ${this.no}호 ${this.name}점입니다!`;
  }
}

console.log(YalcoChicken('홍대', 30));
```
<div align="center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/cc6c1e16-a547-4483-87fc-69ad71362f29">
</div>

  - function으로 선언된 함수는 기본적으로 생성자 함수의 기능을 가짐
<div align="center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/9ee4dbdb-f245-4907-b1cc-0b7eca3a7c12">
</div>

```js
function createYalcoChicken (name, no) {
  return {
    name, no,
    introduce () {
      return `안녕하세요, ${this.no}호 ${this.name}점입니다!`;
    }
  }
}

const chain1 = createYalcoChicken('판교', 3);
const chain2 = createYalcoChicken('강남', 17);
const chain3 = createYalcoChicken('제주', 24);

console.log(chain1, chain1.introduce());
console.log(chain2, chain2.introduce());
console.log(chain3, chain3.introduce());
```
<div align="center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/8ae7c3fa-be10-4b5d-acbd-461245b6d62e">
</div>

-----
### 생성자 함수로 만들어진 객체
-----
1. 프로토타입(Prototype) : 자바스크립트는 객체지향의 중심
```js
function YalcoChicken (name, no) {
  this.name = name;
  this.no = no;
  this.introduce = function() {
    return `안녕하세요, ${this.no}호 ${this.name}점입니다.!`;
  }
}

const chain1 = new YalcoChicken('판교', 3);
console.log(chain1);
```

```js
// 본사에서 새 업무를 추가
// 프로토타입: 본사에서 배포하는 메뉴얼이라고 이해
YalcoChicken.prototype.introEng = function () {
  return `Welcome to Yalco Chicken at ${this.name}!`;
};
```
  - chain1이 생성된 시점에서, prototype을 통해 새로운 기능 추가 가능
  - 즉, 생성자 함수는 인스턴스들과 유기적으로 prototype과 연결

```js
console.log(chain1.introEng());
```

```js
console.log(new YalcoChicken('강남', 17).introEng());
```
<div align="center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/1ff4e344-f523-4198-97c1-a7220193bba3">
<img src="https://github.com/sooyounghan/Web/assets/34672301/613f0081-ccd0-4aa0-8d61-62810e91f103">
</div>

  - 새로 생성되는 객체 또한, prototype으로 정의한 기능 사용 가능

2. 타 언어의 클래스와 다르며, 사용하기에 더 강력함
3. 사실 introduce(Instance)와 introEng(Prototype)은 종류가 다름
<div align="center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/2ad67c97-eba4-4364-b74f-f38f5c96c457">
</div>

-----
### 타 방식으로 만든 객체와의 차이
-----
```js
// 생성자 함수
function YalcoChicken(name, no) { 
  this.name = name;
  this.no = no;
  this.introduce = function() {
    return `안녕하세요, ${this.no}호 ${this.name}점입니다.!`;
  }
}

// 객체 직접 반환
function createYalcoChicken(name, no) {
    return {
    name, no,
    introduce () {
      return `안녕하세요, ${this.no}호 ${this.name}점 입니다.!`;
    }
  }
}

// 객체 리터럴
const chain1 = {
  name : '판교', no : 3,
  introduce : function() {
    return `안녕하세요, ${this.no}호 ${this.name}점입니다.!`;
  }
};

// 객체 반환 함수
const chain2 = createYalcoChicken('강남', 17);
const chain3 = new YalcoChicken('제주', 24);
```

```js
console.log(chain1, chain1 instanceof YalcoChicken);
console.log(chain2, chain2 instanceof YalcoChicken);
console.log(chain3, chain3 instanceof YalcoChicken);
```
<div align="center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/d09924c7-f8e0-4e19-8d93-29967154abd4">
<img src="https://github.com/sooyounghan/Web/assets/34672301/5a7536a9-5156-40e8-98e4-cbf5c65f096f">
</div>

1. 객체 자체의 로그도 상세가 다름 유의(앞에 생성자 함수명이 붙음)
2. instanceof : 객체가 특정 생성자 함수에 의해 만들어졌는지 여부 반환
3. 프로토타입의 constructor의 Chain이 해당 생성자 함수 포함하지는지 여부 : 콘솔에서 [[Prototype]] 펼쳐서 확인

-----
### 생성자 함수 자체의 프로퍼티 함수
-----
```js
function YalcoChciken(name, no) {
  this.name = name;
  this.no = no;
  this.introduce = function() {
    return `안녕하세요, ${this.no}호 ${this.name}점 입니다!`;
  }
}

YalcoChicken.brand = '얄코치킨';
YalcoChicken.contact = function () {
    return `${this.brand}입니다. 무엇을 도와드릴까요?`;
};

const chain1 = new YalcoChicken('판교', 3);
```
  - chain1이라는 인스턴스 생성
  - 하지만, YalcoChicken에 brand와 contact 추가 (즉, 생성자 함수 자체에 기능 추가) [= Java의 Static 개념]
  - 따라서, chain이라는 인스턴스에 적용한 것이 아닌, 생성자에 추가한 것이기 때문에, 생성자 함수에만 적용
    
```js
console.log(YalcoChicken.contact());

consoe.log(chain1.contact());
```
<div align="center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/35aeab2f-4099-44ed-9d07-b516f42dcef7">
</div>

-----
### new 생략 실수 방지하기
-----
```js
function YalcoChicken(name, no) {
  this.name = name;
  this.no = no;
  this.introduce = function() {
    return `안녕하세요, ${this.no}호 ${this.name} 점입니다.!`;
  }

  if(!new.target) {
    return new YalcoChicken(name, no);
  }
}

const chain1 = new YalcoChicken('판교', 3);
const chain2 = YalcoChicken('강남', 17);

console.log(chain1, chain2);
```
<div align="center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/f9c4826c-7296-4ee1-a833-8eb25856ed40">
<img src="https://github.com/sooyounghan/Web/assets/34672301/06250e95-8ef9-451f-8f64-7f08898b2062">
</div>

  - 해당 함수가 new 연산자 없이 호출되었을 경우 조건 확인(!new.target) 재귀호출을 통해 생성해 내보냄

