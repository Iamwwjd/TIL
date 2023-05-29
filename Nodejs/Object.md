# Object

객체와 배열 모두 정보를 정리하는 용도이다.

베얄 : 정보를 `순서에 따라` 정리한다. 이때 배열에 있는 정보들은 숫자로 고유한 식별자를 준다.

객체 : `순서가 없는` 정보를 저장하기에 최적화 되어있다. 숫자로 식별자를 주는것이 아닌 이름으로 고유한 식별자를 준다.

```jsx
// Array
var members = ['060504', 'Jeongyun'];
console.log(members[1]); // Jeongyun

// Object
var roles = {
    'YOB' : '060504', // 이름으로 식별자 지정
    'name' : 'Jeongyun'
}
console.log(roles.name) // Jeongyun

배열은 []를 쓰고 객체는 {}를 쓴다.
```

### 객체_반복

Object에 담겨있는 정보를 하나씩 꺼내 반복문으로 만들어보겠다.

```jsx
# 배열 + 반복 출력
var i = 0;
while(i < members.length){
    console.log(members[i])
} // 060504 Jeongyun

# 앞에 글자를 추가하고 싶을때
var i = 0;
while(i < members.length){
    console.log('hello', members[i])
} // hello 060504 hello Jeongyun
```

```jsx
# 객체 + 반복 출력
for (var name in roles){
    console.log(name)
} // YOB name

: in 앞에 있는 변수에는 객체의 key가 들어오도록 약속되어있다.

# 객체에 있는 내용을 출력하고 싶을때
for (var name in roles){
    console.log(roles[name]);
} // 060504 Jeongyun
```