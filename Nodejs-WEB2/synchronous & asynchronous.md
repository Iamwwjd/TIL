# synchronous & asynchronous

**동기적과 비 동기적의 차이와 의미**

한가지 일이 끝날때까지 기다렸다가 다른 일을 순서대로 하는것이 동기이고(직렬),

한가지 일을 시켜놓고 다른 일을 처리하는 것이 비동기이다.(병렬) → 동시에 일 처리 가능 == 효율적

### 비동기

```jsx
동기적 예시

console.log('A');
var result = fs.readFileSync('syntax/sample.txt', 'utf8') // syntax 밖에서 명령 실행 / sample.txt안에는 B를 넣어놓음
console.log(result);
console.log('C');

순서대로 ABC가 출력됨.
```

```jsx
비동기적 예시

console.log('A');
fs.readFile('syntax/sample.txt', 'utf8', function (err, result){ //err가 있다면 err 출력, result은 파일의 내용을 인자로 출력
    console.log(result);
}) 
console.log('C'); // readFile이 실행될 동안 C출력

fs.readFile이 실행되기 전에 C를 먼저 출력해 ACB로 출력됨.
```

`readFileSync` 는 return 값을 주는데 `readFile`은 return 값이 없기에 var을 쓰면 안되고 함수를 세번째 인자로 주어야 한다.