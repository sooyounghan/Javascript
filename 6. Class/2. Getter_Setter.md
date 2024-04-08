-----
### 접근자 프로퍼티
-----
1. getter : https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Functions/get
2. setter : https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Functions/set
3. getter, setter 함수라고도 부름
4. 스스로는 값을 갖지 않으며, 다른 프로퍼티의 값을 읽거나 저장할 때 사용
5. get, set을 앞에 붙임
```js
const person1 = {
  age : 17, // 데이터 프로퍼티

  get koreanAge () {
    return this.age + 1;
  },

  set koreanAge (krAge) {
    this.age = krAge - 1;
  }
}

console.log(person1, person1.koreanAge);
```

<div align="center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/627183ac-5195-44fb-8ae5-5b1a724386c5">
</div>

```js
person1.koreanAge = 20;

console.log(person1, person1.koreanAge);
```
<div align="center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/31c73b75-fe1b-4561-a1eb-ce42beb36546">
</div>

6. 함수처럼 지정되었으나 프로퍼티처럼 사용
7. 클래스에서도 사용 가능
```js
class YalcoChicken {
  constructor (name, no) {
    this.name = name;
    this.no = no;
  }

  get chainTitle() {
    return `${this.no}호 ${this.name}점`;
  }

  set chainNo(chainNo) {
    if(typeof chainNo !== 'number') return;
    if(chainNo <= 0) return;
    this.no = chainNo;
  }
}

const chain1 = new YalcoChicken('판교', 3);
console.log(chain1.chainTitle);
```
<div align="center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/82ddb871-34ce-486d-901a-9d7b1f097e73">
</div>

```js
chain1.chainNo = '4';
console.log(chain1);
```

```js
chain1.chainNo = -1;
console.log(chain1);
```

```js
chain1.chainNo = 4;
console.log(chain1);
```
<div align="center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/4f851ac4-f702-4cd3-86e0-1fc3c8a273d9">
</div>

  - 클래스에서는 Prototype이 됨 (콘솔에서 객체의 [[Prototype]]에서 확인해볼 것)

-----
### getter
-----
1. 반드시 값을 반환해야 함
2. 특정 프로퍼티(들)를 원하는 방식으로 가공하여 제공할 때 사용

-----
### setter
-----
1. setter는 하나의 인자를 받음
2. 특정 프로퍼티 값이 저장되는 방식을 조작하거나 제한하는데 사용

-----
### 필드 이름과 setter의 이름이 같다면?
-----
```js
class YalcoChicken {
  constructor (name, no) {
    this.name = name;
    this.no = no;
  }

  get no () {
    return this.no + '호점';
  }

  set no (no) {
    this.no = no;
  }
}

const chain1 = new YalcoChicken('판교', 3);
```

  - 무한 반복 오류 발생
<div align="center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/5f2e699b-5119-497d-af99-22faae66e52c">
</div>

  - 해결책
```js
class YalcoChicken {
  constructor (name, no) {
    this.name = name;
    this.no = no;
  }
  get no () { 
    return this._no + '호점'; 
  }
  set no (no) { 
    this._no = no;
  }
}

const chain1 = new YalcoChicken('판교', 3);

console.log(chain1);
console.log(chain1.no);
```
<div align="center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/92f9d496-723e-4e6e-95b2-880287981b1d">
</div>

  - 자동적으로 getter와 setter가 no를 해석해서 _no으로 변경
  - setter와 다른 필드명을 사용해 자기반복 호출 방지


