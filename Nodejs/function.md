중복되는 코드가 불 규칙적으로 나올때 함수가 필요하다.

```jsx
**생성**
function 함수명(){
	//중복되는 코드
}

호출
함수명();
```
### 함수의 입력

```jsx
//자바스크립트가 기본적으로 가지고 있는 함수
//Math.round 숫자를 반올림 시켜준다.
console.log(Math.round(1.7)); // 2

//sum(n1,n2); n1과 n2의 값을 더해준다.
function sum(first, second){ //first, second는 매개변수 parameter
    console.log(first + second) //12
}

sum(5,7); // 각긱의 입력값을 argument라고 한다
```