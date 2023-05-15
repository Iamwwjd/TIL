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

### Boolean

Boolean은 True와 False, 2개의 데이터 타입으로 이루어져 있는데

이때 true와 false는 데이터타입으로 지정되어 있기 때문에 변수로 사용할 수 없다.

Boolean의 데이터 타입은 아래와 같이 표현할 수 있다.

```jsx
console.log(true);
console.log(false);
```

### comparison

**비교연산자** : 

`==` 는 좌항과 우항의 값을 비교해 맞으면 True 다르면 False를 출력하는 표현식이다.

```jsx
console.log(1==1); //true
console.log(1==2); //false

console.log(1>2); //false
console.log(1<2); //true

console.log(1===1); //true
console.log(1===2); //false
```

💡 `=` 은 대입연산자이고 `==` 은 비교연산자이다. 헷갈리지 않기!

### Array data type

배열을 표현할때는 [로 시작해서 ]로 끝나야 한다.

생성, 출력

하나의 배열 안에 내가 수납하고 싶은 데이터를 , 로 구분하여 넣는다 var arr = `['a','b',3,true]`

이를 출력할때는 console.log() ()안에 내가 넣고싶은 배열 데이터를 넣는다.

- 배열에서는 0부터 자릿수가 카운팅 된다!

```jsx
var arr = ['A', 'B', 'C', 'D'];
console.log(arr[1]);

B
```

수정

배열을 수정할때에는 arr[n] = n; 으로 수정이 가능하다.

- 배열의 개수를 셀때는 1부터 측정 (자릿수와 다름!)

```jsx
arr[2] = 3;
console.log(arr);

A 3 C D
console.log(arr.length); // 배열의 길이를 출력한다.
4
```

추가 

배열의 값을 추가할때는 배열명.push(’추가할 값’); 을 넣으면 된다.

```jsx
arr.push('E');
console.log(arr);

A 3 C D Eㄷ
```


### Array & loop

배열과 반복문을 같이 쓰면 유용하게 사용이 가능하다.

```jsx
var number = [1, 50, 4, 700, 11];
var i = 0;
var total = 0;

while(i < 5){
    total = total + num[i];
    i = i + 1;
}
console.log (`total : ${total}`)
```

위와 같이 반복문과 배열을 같이 사용하게 되면

반복문이 끝난 후 콘솔에 변수 number 값의 합이 출력되게 된다.