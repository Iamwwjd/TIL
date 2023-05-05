# program

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

프로그램은 크게 입력을 받아 정보를 처리한 후 그 결과를 출력하는 기계라고 말할 수 있다.

Parameter : 형식이 있는 입력되는 정보

Argument : 형식에 맞게 실제로 입력되는 값