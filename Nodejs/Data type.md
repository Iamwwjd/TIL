# Data type

## Number

**이항연산자** : 왼쪽에 있는 값과 오른쪽에 있는 값을 처리하여 하나의 값을 만드는 역할

```jsx
console.log(3+5); 8
console.log(10-2); 8
console.log(4*2); 8
console.log(16/2); 8
```

## String

문자열을 표현할땐 “ 로 묶어준다. 

이항연산자 양 쪽에 문자열이 존재하면 node.js는 ‘+’를 산술 연산자가 아닌 결합 연산자로 변경한다.

```jsx
console.log('1'+'1'); 11
```

문자열의 개수를 세고 싶을땐 문자열 끝에 `.length` 를 붙여준다

```jsx
console.log('abcdefghigklmnop'.length); 16
```

## Variable
`=` 은 **대입연산자**이다. (오른쪽에 있는 값을 왼쪽에 있는 변수에 대입)

```jsx
var a = 1;
console.log(a); 1
```

변수를 처음 만들때 변수 앞에 var을 붙여주는것이 좋고 그 이후 변수 값을 바꿀 땐 붙이지 않는다.

### 변수의 활용

변수의 대표적 의미 : 데이터에 이름을 붙인다!

```jsx
var alphabet = 'abcdefghijklmnop'
console.log(alphabet); abcdefghijklmnop
```

위 문자열이 알파벳을 나타낸다는것을 변수 이름을 통해 쉽게 알 수 있다.

중복되는 문자열이 많아질 수록 가독성이 떨어진다. 

```jsx
var name = 'hi'
var letter = name + ' jeongyun ' + name + ' jooeun hi jumi ' + name + ' ain';
console.log(letter);
```

이를 변수를 통하여 해결할 수 있다! (바뀌면 안되는 값은 변수로 작성할 필요가 없다)