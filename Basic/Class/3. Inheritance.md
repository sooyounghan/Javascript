-----
### 상속 (Inheritance)
-----
1. 서로 다른 클래스나 생성자 함수가 같은 속성을 공유할 때, 이들의 관계를 정의함으로써 코드 중복을 줄이고 효율을 높임
2. 즉, B 클래스는 A 클래스에서 파생되는 개념 (B는 A의 하위분류)

-----
### 클래스 상속 문법
-----
<div align="center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/12b67c36-902a-4496-86d2-a0bdec5890e5">
</div>

```js
class Bird {
  wings = 2;
}

class Eagle extends Bird {
  claws = 2;
}

class Penguin extends Bird {
  swim () { console.log('수영중..'); }
}

class EmperorPenguin extends Penguin {
  size = 'XXXL';
}

const birdy = new Bird();
const eaglee = new Eagle();
const pengu = new Penguin();
const pengdol = new EmperorPenguin();

console.log(birdy, eaglee, pengu, pengdol);
```
<div align="center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/06a873a2-10c6-49bb-93a0-feda71ce8a25">
<img src="https://github.com/sooyounghan/Web/assets/34672301/dd50d418-237a-4ac0-bd06-151ea332e1a0">
</div>

```js
for (const i of [
  [ '1.', birdy instanceof Bird ],
  [ '2.', eaglee instanceof Bird ],
  [ '3.', eaglee instanceof Eagle ],
  [ '4.', pengdol instanceof Penguin ],
  [ '5.', pengdol instanceof Bird ],
  [ '6.', birdy instanceof Eagle ]
]) {
  console.log(i[0], i[1]);
}
```
<div align="center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/0f207448-0ee8-43fc-9ab8-36b2de69b545">
</div>

```js
pengu.swim();
pengdol.swim();
eaglee.swim();
```
<div align="center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/7d4ede3e-2e88-48e6-96b3-ecc4bac7a1ce">
</div>

1. 클래스에서는 extends (부모클래스)로 상속관계 정의
2. 자식 클래스에서 또 다른 클래스가 상속 받을 수 있음
3. 자식 클래스는 부모 클래스의 속성을 기본적으로 가져옴
4. 자식 클래스의 인스턴스는 부모 클래스의 인스턴스로 인식됨
5. [[Prototype]]으로 상속 관계를 살펴볼 것 : 최종적으로 가장 위는 Object
6. 자바스크립트는 상속 관계도 결국 Prototype을 통해 구현

```js
class YalcoChicken {
  no = 0;
  menu = { '후라이드': 10000, '양념치킨': 12000 };

  constructor (name, no) {
    this.name = name;
    if (no) this.no = no;
  }
  introduce () {
    return `안녕하세요, ${this.no}호 ${this.name}점입니다!`;
  }
  order (name) {
    return `${this.menu[name]}원입니다.`
  }
}
```

```js
class YalcoChickenAndCafe extends YalcoChicken {
  cafeMenu = { '아메리카노': 4000, '라떼': 4500 };
  cafeOrder (name) {
    return `${this.cafeMenu[name]}원입니다.`
  }
}

const chain1 = new YalcoChickenAndCafe('서면', 2);
console.log(chain1);
console.log(
  chain1.order('후라이드'),
  chain1.cafeOrder('라떼')
);
```
<div align="center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/a3d08780-67ee-4f97-a1db-e303fdad57ea">
<img src="https://github.com/sooyounghan/Web/assets/34672301/118d23bb-9ab5-4f8b-a6ae-14478146132a">
<img src="https://github.com/sooyounghan/Web/assets/34672301/89ad4af4-5bd4-410f-a1a2-b9eab5b838a2">
</div>

-----
### 오버라이딩 (Overriding)
-----
1. 자식 클래스에서 부모로부터 물려받은 속성이나 기능을 덮어씀
```js
class Bird {
  wings = 2;
  canFly = true;
  travel () { console.log('비행중...') }
}
class Eagle extends Bird {
  claws = 2;
}
class Penguin extends Bird {
  canFly = false;
  travel () { console.log('수영중...') }
}

const eaglee = new Eagle();
const pengu = new Penguin();

console.log(eaglee);
eaglee.travel();

console.log(pengu);
pengu.travel();
```
<div align="center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/708cb86b-680a-463a-ad2b-07a32df8b09d">
<img src="https://github.com/sooyounghan/Web/assets/34672301/07f3f669-dbc7-40a8-94dc-0302fe7a0c07">
</div>

```js
class YalcoChicken {
  no = 0;
  menu = { '후라이드': 10000, '양념치킨': 12000 };

  constructor (name, no) {
    this.name = name;
    if (no) this.no = no;
  }
  introduce () {
    return `안녕하세요, ${this.no}호 ${this.name}점입니다!`;
  }
  order (name) {
    return `${this.menu[name]}원입니다.`
  }
}
```

```js
class YorkNannyYalcoChicken extends YalcoChicken {
  introduce () {
    return `또 뭐 쳐먹으러 기어들어왔어.`;
  }
  order (name) {
    return `${this.menu[name]}원이여.`
  }
}

const chain1 = new YorkNannyYalcoChicken ('종로', 48);

console.log(chain1.introduce());

console.log(chain1.order('양념치킨'));
```
<div align="center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/873fdab6-9252-4fe5-bd28-828e9c6b6e79">
</div>

-----
### super
-----
1. https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Operators/super
2. 부모 클래스의 constructor 또는 메서드 호출
```js
class YalcoChicken {
  no = 0;
  menu = { '후라이드': 10000, '양념치킨': 12000 };

  constructor (name, no) {
    this.name = name;
    if (no) this.no = no;
  }
  introduce () {
    return `안녕하세요, ${this.no}호 ${this.name}점입니다!`;
  }
  order (name) {
    return `${this.menu[name]}원입니다.`
  }
}
```

```js
class ConceptYalcoChicken extends YalcoChicken {
  #word = '';
  constructor (name, no, word) {
    super(name, no);
    this.#word = word;
  }
  introWithConcept () {
    return super.introduce() + ' ' + this.#word;
  }
  order (name) {
    return super.order(name) + ' ' + this.#word;
  }
}

const pikaChain = new ConceptYalcoChicken('도봉', 50, '피카피카~');

console.log(pikaChain);
console.log(pikaChain.introWithConcept());
console.log(pikaChain.order('후라이드'));
```
<div align="center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/3751a505-8f7d-4a32-ae31-bf942e8b9009">
<img src="https://github.com/sooyounghan/Web/assets/34672301/3914117c-58a3-4d28-8c39-418f48015cae">
</div>

1. super는 다른 클래스에서 상속 받은 클래스만 사용 가능
2. 자식 클래스의 constructor 내에서는 부모 클래스의 constructor를 가리킴
3. 자식 클래스의 메서드 내에서는 부모 클래스(에서 만들 인스턴스)를 가리킴
4. 부모 클래스의 constructor나 메서드에 추가적 동작을 넣기 위해 사용

5. 정적 메서드에서의 사용
```js
class YalcoChicken {
  static brand = '얄코치킨';
  static contact () {
    console.log(`${this.brand}입니다. 무엇을 도와드릴까요?`);
  }
}

class ConceptYalcoChicken extends YalcoChicken {
  static contact () {
    super.contact();
    console.log('컨셉 가맹문의는 홈페이지를 참조하세요.');
  }
}

ConceptYalcoChicken.contact();
```
<div align="center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/736afdfd-a919-4ceb-b484-9417ca3eb20a">
</div>
