```jsx
# 1
console.log('A');
console.log('B');
console.log('C1');
console.log('D');
```

프로그램을 이렇게 쓰고 node [파일명]을 실행시켜준다면 프로그램은 이를 순차적으로 실행시켜 준다

때에 따라 실행해야 하는 것이 다르다면 조건문을 사용하여 해결할 수 있지만,

우리는 조건문이 아니더라도 다른 파일을 만들어 필요에 따라 다른파일을 실행시켜 해결할 수 있다.

```jsx
#2
console.log('A');
console.log('B');
console.log('C2');
console.log('D');
```

하지만 실행해야할 파일의 양이 그하급수적으로 많아지게 된다면 굉장히 불편할 것이다.

우리는 이를 편리하게 사용하기 위해 조건문을 사용한다.

### Conditional statements

**if문**

```jsx
console.log('A');
console.log('B');
if(true) {
    console.log('C1');
}
if(false) {
    console.log('C2');
}
console.log('D');
```

다음과 같이 실행하면 조건이 ture 이기 때문에 A B 다음 C1이 출력되고 false가 아니기 때문에 C2는 건너뛴 후 D가 출력된다.

또한 조건이 2개일때는 조건 두 개를 다 적지 않고 else를 이용하여 간단히 해결할 수 있다.

```jsx
console.log('A');
console.log('B');
if(true) {
    console.log('C1');
}
else {
    console.log('C2');
}
console.log('D'); // A B C1 D
```
위 코드 맨 윗줄에 아래 코드를 넣고

```jsx
var args = process.argv;
console.log(args)
```

`node syntax/conditional.js jeongyun` conditional 을 실행시켜주고 뒤에 내 닉네임을 적어주면

```jsx
[
  '/usr/local/bin/node',
  '/Users/songjeongyun/Documents/Nodejs/syntax/conditional.js',
  'jeongyun'
]
A
B
C1
D
```

위와 같은 결과가 나오는데 이는 args라는 변수 안에 위와 같은 정보가 들어가 있다는 뜻이다.

위 결과를 분석해보자.

첫번째 줄에는 node.js 런 타임이 어디에 위치해 있는지를 보여주고 

두번째 줄은 우리가 실행시킨 파일에 대한 경로를 주고 있고,

세번째 줄에 우리가 입력한 입력값을 주고 있다. 

컴퓨터 프로그래밍에서는 숫자를 0부터 세는 경우가 많다. 그렇다면 우리가 가져오려는 값은 두 번째 자리에 있는것과 같다. 그렇기 때문에 `console.log(args)`를 `console.log(args[2])`로 바꾸어 실행시켜주면

```jsx
jeongyun
A
B
C1
D
```

이 출력된다. 

이를 응용하여 `node syntax/conditional.js 1`을 넣었을때 if문 값이 true가 되면서 C1이 출력되게 하겠다.

```jsx
var args = process.argv;
console.log(args[2])

console.log('A');
console.log('B');
if(arg[2] === '1') { // arg[2]와 문자 1이 같으면 C1을 출력하게 한다. 여기서 1은 문자이기 때문에 ''를 해준다.
    console.log('C1');
}
else {
    console.log('C2');
}
console.log('D');
```

### Loop statements

반복문

우리가 어떠한 상황에서 같은 구문을 반복해 출력해야할 상황이 생길때

```jsx
console.log('A');
console.log('B');
console.log('C1');
console.log('C2');
console.log('C1');
console.log('C2');
console.log('C1');
console.log('C2');
console.log('D');
```

단순히 여러번 출력을 하는 방법도 있지만 이는 출력해야할 수가 늘어나면 코드가 지저분해진다.

**While 문**

기본 형식

```jsx
// While (Boolean){반복하여 출력할 값}

console.log('A');
console.log('B');

While () {
console.log('C1');
console.log('C2');
}

console.log('D');
```

while의 boolean이 ture 일 때, 반복 구간이 무한출력 된다. *조심!*