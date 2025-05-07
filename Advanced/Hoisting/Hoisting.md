-----
### 💡 호이스팅 (Hoisting)
-----
: ```https://developer.mozilla.org/ko/docs/Glossary/Hoisting```

1. 인터프리터가 코드를 실행하기 전 함수, 변수, 클래스 또는 import 선언문을 해당 범위의 맨 위로 끌어올리는 것처럼 보이는 현상
```js
console.log(hoisted1); // ⚠️ 오류
```
<div align="center">
<img src="https://github.com/sooyounghan/HTTP/assets/34672301/647dd490-5a09-4ca2-87ce-9ee3979d8f00">
</div>

```js
console.log(hoisted1); // 💡 오류발생 X, 대신 undefined 반환

var hoisted1 = 'Hello'; // 엔진이 실행될 때, var hosited1을 맨 위로 끌어올림 (초기화는 아직 진행되지 않았으므로 undefined)

console.log(hoisted1)
```
<div align="center">
<img src="https://github.com/sooyounghan/HTTP/assets/34672301/02095a00-5dbc-4caa-bdb6-11e70b549192">
</div>

```js
console.log(hoisted2); // ⚠️ 오류

let hoisted2 = 'Hello';

console.log(hoisted2)
```
<div align="center">
<img src="https://github.com/sooyounghan/HTTP/assets/34672301/da1db144-e868-4b53-940e-6f87730181ac">
</div>

2. 엄연히는 let / const도 호이스팅되지만 undefined로 초기화되지 않는 것
3. 단, 이들은 초기화되기 이전의 영역 : TDZ에 속함 (```https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Statements/let#%EC%8B%9C%EA%B0%84%EC%83%81_%EC%82%AC%EA%B0%81%EC%A7%80%EB%8C%80```)
  - TDZ (시간상 사각지대, Temproal Dead Zone) : 변수 스코프의 맨 위에서 변수의 초기화 완료 시점까지 변수가 존재하는 곳
  - 따라서, ReferenceError가 발생
    
* var는 다양한 상황에서 예기치 못한 문제를 야기하므로 더 이상 사용하지 않도록 하는 것이 좋음
