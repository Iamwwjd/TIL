# call back

```jsx
function a() {
    console.log('A');
}

function() { // 이름이 없는 함수 -> 익명함수
    console.log('A');
}

var a = function() { // a라는 변수의 값으로 함수를 지정
    console.log('A');
}

function slowfunc(callback){
    callback();
}

slowfunc(a); // a라는 함수를 가르킴 -> a실행
```