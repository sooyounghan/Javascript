-----
### String 객체 - 생성자 함수
-----
: https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/String
1. 생성자 함수
```js
const strObj1 = new String();
const strObj2 = new String('Hello World!');

console.log(strObj1);
console.log(strObj2);
```
<div align="center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/76817a7d-d654-4d9e-b674-6cfdd4350d59">
<img src="https://github.com/sooyounghan/Web/assets/34672301/c80d4141-1552-4ff6-badf-ae88871e3f8b">
</div>

  - 문자열도 유사 배열 객체

```js
console.log(strObj1.valueOf(), strObj1.toString());
console.log(strObj2.valueOf(), strObj2.toString());
```
<div align="center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/5396a140-fc64-4268-8981-415eeee94daa">
</div>

  - valueOf() 또는 toSring() 메서드로 문자열 원시값 반환

```js
const fromNum = new String(123);
const fromBool = new String(true);
const fromArr = new String([1, 'A', false]);
const fromObj = new String({a: 1});

console.log(typeof fromNum, fromNum);
console.log(typeof fromBool, fromBool);
console.log(typeof fromArr, fromArr);
console.log(typeof fromObj, fromObj);

console.log(fromNum.toString());
console.log(fromBool.toString());
console.log(fromArr.toString());
console.log(fromObj.toString());
```
<div align="center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/306d0fd4-e883-47d2-9ab5-a11eb44a90f5">
</div>

  - 다른 타입들도 감쌀 수 있음 (즉, 문자열로 변환한 값을 가진 String 객체 반환)

  - 생성자 키워드 new 없이 사용한다면? 바로 문자열로 바꿀 수 있음
```js
const str1 = String('Hello World!');
const str2 = String(123);
const str3 = String(true);
const str4 = String({x: 1, y: 2}); // 💡 [object Object]
const str5 = String([1, 2, 3]); // 💡 1,2,3

console.log(typeof str1, str1);
console.log(typeof str2, str2);
console.log(typeof str3, str3);
console.log(typeof str4, str4);
console.log(typeof str5, str5);
```
<div align="center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/43976dd2-2843-473e-8907-9be50b10de43">
</div>

  - 생성자로서가 아닌 String 함수는 주어진 인자를 문자열로 변환하여 반환
  - 객체는 string로서의 의미가 없음 ([object Object])
    
-----
### 유사 배열 객체
-----
```js
let myStr = '안녕하세요!';

console.log(
  myStr.length,
  myStr[0],
  myStr[myStr.length - 1]
);
```
<div align="center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/54eb5d30-c91d-4c6c-a91d-56f79e6071e3">
</div>

```js
myStr[myStr.length - 1] = '?';
console.log(myStr); // 💡 배열과 달리 그대로
```
<div align="center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/a7eaec05-a95a-4f14-b824-2ab52ec10685">
</div>

```js
for (const letter of myStr) {
  console.log(letter);
}
```
<div align="center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/dc6a4ae4-0d01-4c08-bd0b-48c204e28de4">
</div>

1. length 프로퍼티 : 글자 수 반환
2. [n] 안에 인덱스 숫자를 넣어 n+1 번째 글자를 읽기'만' 가능
3. for ... of 문 사용 가능 (Iterable이기 떄문임)
4. String은 원시값
   - [] 접근 또는 인스턴스 메서드로 특정 글자만 수정하는 것이 불가능한 이유
   - 수정하려면, 변수 값 자체를 다른 문자열로 대체해야함 (예) myStr = '안녕하세요?'; 또는 +=)
  
-----
### 주요 인스턴스 메서드
-----
* 주의 : 기존의 문자열은 바꾸지 않음!
  
1. toUpperCase, toLowerCase
   - 라틴어 문자를 모두 대문자 / 소문자로 변경하여 반환
```js
const word = 'Hello, World.';
console.log(
  word.toUpperCase(),
  word.toLowerCase()
);

console.log(word);
```
<div align="center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/fbef0217-3d27-4260-9c81-4f4d2c688ffd">
</div>

  - 흔한 활용 예
```js
function areSameWords (word1, word2) {
  return word1.toLowerCase() === word2.toLowerCase();
}

console.log(
  areSameWords('Hello', 'hello'),
  areSameWords('가나다', '가나다'),
  areSameWords('ABC', 'DEF')
);
```
<div align="center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/69102293-557f-4458-815d-17cb820dfdba">
</div>

2. charAt, at
   - 인자로 주어진 인덱스의 문자 반환
```js
console.log(
  'Hello World!'.charAt(0),
  '안녕하세요~'.charAt(2)
);
```
<div align="center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/ca332a6b-f5ca-4b08-b309-170c423e8c6d">
</div>

  - at : 신기능으로, 배열에서도 사용 가능 / 음수로 뒤에서부터 접근 가능 (-1부터 시작)
```js
console.log(
  '안녕하세요~'.at(1),
  '안녕하세요~'.at(-1),
  '안녕하세요~'.at(-2),
  '안녕하세요~'.at(-3)
);
```
<div align="center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/f5024d56-f7b7-43af-8983-4e723d495889">
</div>

3. indexOf, lastIndexOf
   - 인자로 주어진 문자열이 앞, 또는 뒤에서 '처음' / '마지막'으로 등장하는 인덱스 반환
   - 포함되지 않을 시 -1 반환
```js
const word = '반갑습니다!';
console.log (
  word.indexOf('습'),
  word.lastIndexOf('습')
);
```
<div align="center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/9910a11d-484b-43f5-90a1-ce1c88899d9b">
</div>

```js
const word = '아니, 하나마나한 걸 왜 하나?';
console.log (
  word.indexOf('하나'),
  word.lastIndexOf('하나')
);
```
<div align="center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/70928628-2726-467b-ab25-2c430f1ec6c7">
</div>

```js
console.log(
  '가나다라마'.indexOf('하'),
  '가나다라마'.lastIndexOf('하')
);
```
<div align="center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/13b86c35-8372-45d0-a6ea-f2f163585e0f">
</div>

4. includes, startsWith, endsWith
   - 인자로 주어진 문자열을 (아무곳에 / 맨 앞에 / 맨 끝에) 포함 여부 (Booelan으로 반환)
```js
const sentence = '옛날에 호랑이 한 마리가 살았어요.';

for (const word of ['옛날에', '호랑이', '살았어요.', '나무꾼']) {
  console.log(
    'includes', word, sentence.includes(word)
  );
  console.log(
    'startsWith', word, sentence.startsWith(word)
  );
  console.log(
    'endsWith', word, sentence.endsWith(word)
  );
  console.log('- - - - -');
}
```
<div align="center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/ec5e9592-02a0-4e90-a516-dfaba84a4941">
</div>

5. search
   - 인자로 받은 정규표현식과 일치하는 첫 부분의 인덱스 반환
   - 없을 시 -1 반환
```js
console.log(
  '하루가 7번 지나면 1주일이 되는 거야.'.search(/[0-9]/),
  '하루가 일곱 번 지나면 일주일이 되는 거야.'.search(/[0-9]/)
);
```
<div align="center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/c23ac9df-4cec-44e6-b3de-b4d03a2d4b9a">
</div>

6. subString
   - 인자로 전달받은 인덱스(들)을 기준으로 자른 문자열 반환
```js
const word = 'ABCDEFGHIJKL';
const part = word.substring(4, 8)

console.log(word, part);
```
<div align="center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/b173e583-51f5-46d6-a6b1-7b64bd129a4b">
</div>

```js
const word = 'ABCDEFGHIJKL';

console.log(
  word.substring(4)
);

console.log(
  word.substring(-1), // 0부터 시작
  word.substring(4, 100), // 4부터 마지막까지
  word.substring(100) // 마지막부터 시작 (없음)
);
```
<div align="center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/58646f28-c869-4f40-b4c7-48a392c2e3eb">
</div>

  - 인자를 하나만 넣으면 해당 인덱스부터 끝까지 진행
  - 음수나 범위 외 숫자는 범위 내 최소 / 최대 숫자로 변환

```js
const sentence = '옛날에 호랑이 한 마리가 살았어요.';

const firstWord = sentence.substring(
  0, sentence.indexOf(' ')
);
const lastWord = sentence.substring(
  sentence.lastIndexOf(' ') + 1, sentence.length
);

console.log(firstWord, lastWord);
```
<div align="center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/6df80980-1c6e-443b-b7c7-9d02719bbd04">
</div>

7. slice
   - subString과 같으나 음수로 뒤에서부터 자를 수 있음
```js
const word = 'ABCDEFGHIJKL';
console.log(
  word.substring(4, 8),
  word.slice(4, 8),
);

console.log(
  word.substring(-4),
  word.slice(-4)
);
```
<div align="center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/1a63f1df-4a68-4f42-ac4a-724958ece764">
</div>

```js
const sentence = '옛날에 호랑이 한 마리가 살았어요.';

const firstWord = sentence.slice(
  0, sentence.indexOf(' ')
);

const lastWord = sentence.slice(
  sentence.lastIndexOf(' ') + 1 - sentence.length
);

console.log(firstWord, lastWord);
```
<div align="center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/cb969f82-8c5a-4cf4-9b7c-c157f7c90b06">
</div>

8. split
   - 인수로 주어진 문자열이나 정규표현식으로 분리하여 '배열' 반환
```js
console.log(
  '010-1234-5678'.split('-'),
  'ABC1DEF2GHI3JKL'.split(/[0-9]/)
)
```
<div align="center">
<img  src="https://github.com/sooyounghan/Web/assets/34672301/468c9d96-603e-4e86-9f5e-75f1b1dec005">
</div>

```js
// 인자로 빈 문자열을 넣거나 인자 생략시
const word = '안녕하세요';

console.log(
  word.split(''), // 빈 문자열 : 한 글자씩 반환
  word.split(), // 자체 하나의 문자열로 반환
  word.split('A') // 없는 문자열을 넣으면 전체 문자열 반환
)
```
<div align="center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/f20205cd-50a9-4523-871f-922a17f5d4be">
</div>


```js
const word = '하나 하면 할머니가 지팡이 짚고서 잘잘잘';

console.log(
  word.split(' ', 2), // 2번째 split까지만 동작하여 가져옴
  word.split(' ', 4) // 4번째 split까지만 동작하여 가져옴
)
```
  - 두 번째 인자로 배열의 최대 길이 지정 가능
<div align="center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/b1bc0df3-4571-45b1-8b25-425571687626">
</div>


```js
const sentence = '옛날에 호랑이 한 마리가 살았어요.';
const splitted = sentence.split(' ');

const firstWord = splitted[0];
const lastWord = splitted[splitted.length - 1];
// const lastword = splitted.at(-1);

console.log(firstWord, lastWord);
```
<div align="center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/e6342c70-3c8d-4e70-8113-67c35ef2613d">
</div>


9. trim, trimStart, trimEnd
  - 앞 뒤 공백 제거해 반환
```js
const word = '  Hello World!  ';
console.log(`--${word}--`); // 앞 / 뒤 공백 존재 
console.log(`--${word.trim()}--`); // 앞 / 뒤 공백 제거 
console.log(`--${word.trimStart()}--`); // 앞 공백 제거
console.log(`--${word.trimEnd()}--`); // 뒤 공백 제거
```
<div align="center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/12991022-f15b-4113-a4ab-8aba30df5891">
</div>

  - 중간의 공백은 제거하지 않음

10. repeat
    - 인자로 주어진 정수만큼 문자열을 반복하여 반환
```js
const word = '호이';

console.log(word.repeat(3));
console.log(word.repeat(0)); // 빈 문자열 반환
console.log(word.repeat()); // 빈 문자열 반환
```
<div align="center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/fc6ec21e-f883-40e8-94d0-cd23c2323ea8">
</div>

```js
console.log(word.repeat(-1)); // 오류 발생
```
<div align="center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/bf66140c-5579-46fe-9597-d9f604d1f61c">
</div>

  - 인수가 없거나 0이면 빈 문자열 반환, 음수면 오류발생

11. replace, replaceAll
  - 첫 번째 인자로 받은 문자열 또는 정규식을 두 번째 인자로 치환한 결과 반환
```js
console.log(
  '이스탄불은 터키의 수도이다.'.replace('터키', '튀르키예')
);
```
<div align="center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/e401b477-8ea9-4b0d-868b-9be27058d9b1">
</div>

```js
const word = '밥 좀 먹자, 밥. 응? 야, 밥 좀 먹자고 밥, 밥!';

console.log(word.replace('밥', '라면'));
console.log(word.replace(/밥/g, '라면'));
```
  - replace의 첫 인자가 문자열이면, 일치하는 첫 부분만 치환
  - 모두 치환하려면 정규식 /.../g (따옴표 없음)
<div align="center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/86fd8140-6cd0-42fc-9a54-e7c6027f961c">
</div>

```js
console.log(word.replaceAll('밥', '라면'));
console.log(word.replaceAll(/밥/g, '라면'));
```
  - replaceAll은 문자열도 자동으로 /.../g처럼 인식
<div align="center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/9d588fc8-30c3-428d-b0ac-69b4b906bb8c">
</div>

-----
### 메서드 체이닝 (Metnod Chaining)
-----
1. 값을 반환하는 인스턴스 메서드를 연속으로 사용
2. 예제
```js
const word = ' 모두 HELLO! ';
const rpFrom = 'hello';
const rpTo = 'bye';

console.log(
  word
  .trimStart()                // '모두 HELLO! '
  .toLowerCase()              // '모두 hello! '
  .replaceAll(rpFrom, rpTo)   // '모두 bye! '
  .toUpperCase()              // '모두 BYE! '
  .repeat(3)                  // '모두 BYE! 모두 BYE! 모두 BYE! '
  .trimEnd()                  // '모두 BYE! 모두 BYE! 모두 BYE!'
);

console.log(word); // 원본은 그대로
```
<div align="center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/1e8e2c5e-f1c2-442e-b6f5-ee45cc6bf3ce">
</div>
