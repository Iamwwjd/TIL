# Template Literal

<aside>
💡 여기서 Literal 이란 정보를 표현하는 방법, 기호이다.

</aside>

문자 안에서 줄바꿈을 사용하고 싶을 때 사용할 수 있는 두가지 방법이 있는데, 

1. **줄바꿈을 하고싶은 부분에  `\n` 을 쳐준다.**

```jsx
var name = 'hi'
var letter = name+ ' jeongyun ' + name + '\n\njooeun hi jumi ' + name + ' ain';
console.log(letter);
```

1. **문자열 시작 부분에 ‘ 가 아닌 ` 를 사용해주고 ${변수명}으로 변수를 감싸준 뒤 줄바꿈을 하고싶은 부분에는 그냥 enter를 쳐준다.**

```jsx
var name = 'hi'
var letter = `${name} jeongyun ${name}

jooeun hi jumi ${name}  ain`;
console.log(letter);
```

${}을 사용하면 {}안에 있는 내용을 알아서 치환하여 실행시켜준다.

*ex)* 

```jsx
var name = 'hi'
var ID = `${name} my Student number is ${1+1}1${0}6`;
console.log(ID)
```

*두가지 방법 다 사용할 수 있지만 편리함과 가독성 때문에 두 번째 방법을 사용하는 것이 좋다*