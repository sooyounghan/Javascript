-----
### Console
-----
1. 자바스크립트의 기능이 아닌 환경의 기능
   - 브라우저 : Web API 기능 중 하나
   - Node.js : 디버깅을 위한 모듈 (브라우저의 콘솔과 유사하게 동작)
   - 소프트웨어 외적으로는 영향을 끼치지 않음 (개발자용 기능)
   - 콘솔을 열어 확인하지 않는 이상 보이지 않음

2. 흔히 활용되는 console 기능
- console.log()
```js
console.log('로그 - 기본적인 출력');
```
- console.info()
```js
console.info('로그 - 기능적으로는 log와 같으나 사용하기에 따라 용도 구분 가능');
```
- console.warn()
```js
console.warn('경고 - 문제가 될 수 있는 부분');
```
- console.error()
```js
console.error('오류 - 에러 발생 상황');
```
<div align = "center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/8731210e-a8c2-4c82-9114-e5eec66c89a7">
</div>

-----
### Console 예시
-----
1. 콘솔에 데이터 출력
```js
console.log(로그에_출력할_값);
console.log(값1, 값2, 값3, ...);
```

2. 예시
```js
console.log('Hello World!');
console.log(1);
console.log({Name : '홍길동', age : 20, married : false});
console.log('Hi!', 100, true, [1, 2, 3]);
```
<div align="center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/3f29cfa5-64f6-4009-b728-a73e04a7a0bc">
</div>

3. 단순한 값 뿐만 아니라, {Name : '홍길동', age : 20, married : false}와 같은 객체도 가능
4. 쉼표를 이용하면, 공백이 구분자가 되어 출력

-----
### Node.js의 REPL 사용
-----
1. REPL (Read Eval Print Loop)
2. node 명령어로 JavaScript의 명령 입력 모드 진입 후 입력
3. 모드 종료 : Ctrl + c 2회
4. Terminal Clear : clear

-----
### Node.js 환경에서 .js 파일 실행
-----
1. VS Code에서 프로젝트 폴더 열람
2. Visual Code에서 작성한 JS 파일 실행
   - 2번과 동일하게 Terminal 진입
   - node 실행할 JS파일 (예) node index.js) [Terminal의 현재 경로는 파일이 존재하는 경로에 위치]
<div align="center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/7fc6eab8-6dda-42de-8c0a-cb99e59a72f0">
</div>


3. Code Runner 확장 기능 사용 (Ctrl + Alt + N)
<div align="center">
<img src="https://github.com/sooyounghan/Web/assets/34672301/de99d7cb-7038-4a50-8881-e43b7ba9068a">
</div>
      
