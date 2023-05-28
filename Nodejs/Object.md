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