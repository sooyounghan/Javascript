-----
### 변수(let)와 상수(const)
-----
```js
console.log('Hello', '철수');
```
: 일회용으로 해당 값들을 사용 가능

1. 데이터를 담는 곳
```js
// 값들을 변수와 상수에 담아 사용
const SALUTATION = 'Hello, ';
let person = '철수';

console.log(SALUTATION, person);
```
<div align="center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/bf34f086-e1fc-4d66-af89-0328a8d19abb">
</div>

```js
let person = '영희';

console.log(SALUTATION, person);
```
<div align="center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/d56e60d9-0dbb-4c14-ba9a-8b05654f9736">
</div>

2. 변수와 상수의 목적
   - 값의 의미를 나타내는 역할
   - 값의 재활용이 가능
   - 변경되는 상태를 가리키는 식별자
  
-----
### 변수(variable)
-----
1. 담긴 값을 변경 가능한 것
2. let 사용
3. 예시
   - x란 변수를 선언 후, 값을 넣음
```js
let x;
console.log(x);
```
<div align="center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/5f0acdf2-a1bc-4dbd-a39d-943fd4d63605">
</div>

  - undefined 출력 : '아직 값이 정해지지 않았다'라는 값을 의미
    
<div align="center">
<img src ="https://github.com/sooyounghan/Web/assets/34672301/93bb1fe8-205e-4077-9f2a-50589958e20d">
</div>

   - let x; : 변수 영역에 x라는 메모리 공간이 할당
   - 이 때, 메모리의 데이터 영역에 undefined의 영역을 x가 가리키게 됨

```js
x = 1;
console.log(x);
```

<div align="center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/c803f876-a136-4e07-b374-45ee8f27e397">
</div>

<div align="center">
<img src = "https://github.com/sooyounghan/Web/assets/34672301/3fd849ce-ae7e-4099-ace3-cd924ab80725">
</div>

   - x = 1;
   - 값을 넣어주게 되면, 메모리 영역의 1라는 공간이 차지하고 있는 공간에 대해 x가 가리킴

4. 주로, 변수에 대한 초기화를 일반적으로 사용함
```js
let x = 1;
console.log(x);
```
  - 하지만, 메모리 상으로는 선언과 초기화를 따로 하는 것과 동일
  - 즉, undefined 할당 후, 재할당하는 것

5. 다른 변수가 같은 값을 가질 때
```js
let x = 2;
let y = x;

console.log(x, y);
```
<div align="center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/00e0fa34-b0a2-46f6-a5f1-50399ff7810e">
</div>

<div align="center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/b937689c-fa24-418c-8ed3-82c9f4d23cf8">
</div>

  - y도 처음에 undefined를 가리키다가, x와 동일한 1이 저장된 데이터 영역의 주소를 가리킴
  - 같은 값이 다른 데이터 영역에 저장되지 않음
  - 즉, 메모리 절약 (변수가 여러 개여도 식별자 1개만 가리키게 됨)

6. x에 2을 넣은 뒤, 값을 'Hello!'로 변경
```js
let x = 2;
let y = x;

console.log(x, y);
```

```js
x = 'Hello!';

console.log(x, y);
```
<div align = "center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/67ee7e16-c3ee-4e38-a17f-00010ad7f33a">
</div>

<div align="center">
<img src = "https://github.com/sooyounghan/Web/assets/34672301/a70c67bc-947f-4989-b845-c10bac279469">
</div>

  - 다른 언어와 달리, 메모리 상 가리키는 위치가 변경 (즉, 기존 위치에 값을 넣는 것이 아님)
  - x = 'Hello!'로 변경됨에 따라, 데이터 영역에 'Hello!'의 공간이 할당되고, 이를 가리킴
  - y는 동일하게 아직 1을 가리키므로, 데이터 영역의 1이 할당된 공간을 가리킴
  - JavaSrcipt는 데이터의 종류에 관계 없이 그 종류를 자료형이라고 함 (어떤 값이든 가능)
  - 자료형마다 데이터 크기가 다르므로, 차지하는 공간이 변경된 크기의 데이터와 일치하지 않을 수 있으므로 위와 같이 동작

7. let : 재선언 불가
```js
let x = 1;
console.log('첫 선언', x);

let x = 2;
console.log('재 선언', x);
```
<div align="center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/53238400-c727-4932-8366-301bcf61e4f7">
</div>

```js
let x = 1;
console.log('첫 선언', x);

x = 2;
console.log('재 선언', x);
```
<div align="center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/8dac43cc-2138-4fec-8059-3cffa9cb030b">
</div>

8. 선언하기 전 코드를 사용할 수 없음
```js
console.log(xyz);
let xyz = 3;
```
<div align="center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/7b26ae0b-af87-47a9-9ecf-965f60f93e38">
</div>

-----
### 상수 (Constant)
-----
1. 변수와 달리 선언된 값이 변경될 수 없음
2. const 키워드 사용
3. 흔히 대문자로 명명 (여러 곳에 사용될 공통 값인 경우)

4. 상수를 선언과 동시에 초기화
```js
const PI = 3.14;
console.log('원주율', PI);
```
<div align="center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/ffaa3f02-ea43-4880-babc-50664f963f9b">
</div>


5. 선언만 하는 것은 불가
```js
const PI;
PI = 3.14;
```
<div align="center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/164ed7e1-ffae-41e2-bb0e-16cbdf649270">
</div>

6. 상수는 값의 변경이 불가
```js
const PI = 3.14;
PI = 3.14159;
```
<div align="center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/95e1fcf6-400e-468f-9266-7810d79c46b0">
</div>

7. 값이 바뀔 일이 없는 데이터는 상수로 선언할 것

-----
### 여러 변수와 상수 동시에 선언
-----
```js
let a = 1, b = 2, c = 3;
const X = 4, Y = 5, Z = 6;

console.log(a, b, c);
console.log(X, Y, Z);
```
<div align="center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/3e6ddae5-366a-4028-a0c6-2ceff6be23aa">
</div>

-----
### 브라우저 콘솔 시 특이사항
-----
```js
let x = 2;
let x = 3;
```
  : 한 코드 내에서 재선언 불가

```js
let x = 3;
```

```js
let x = 2;
```
  : 브라우저 콘솔에서 독립적 시행시 같은 이름의 변수와 상수를 재선언 가능
    
```js
const x = 3;
```
  : 단, 변수를 상수로, 상수를 변수로 재선언하면 오류 (새로고침 필요)


-----
### 식별자(Identifier) : 상수와 변수 등의 이름
-----
1. 식별자 명명 규칙
   - 영문, 한글 및 유니코드 글자, 숫자 사용 가능
   - 특수문자는 $ 또는 _ 가능
   - 숫자로 시작 불가
   - 공백(스페이스) 사용 불가
  
2. 예약어 (Reserved Words) : 변수명이나 상수명으로 쓸 수 없는 것
  - 예시
```js
const let = 1;
let typeof = 2;
```

3. 한글 변수 / 상수명 : 가능은 하지만, 되도록 지양
```js
const 이름 = '홍길동';
let 나이 = 20;

console.log(이름, 나이);
```
