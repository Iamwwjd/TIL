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