# Module

mpart

```jsx
var M = {
    v:'v',
    f:function(){
        console.log(this.v);
    }
}

module.exports = M; // 모듈이 담겨있는 Mpart.js 중 var M을 바깥에서 사용할 수 있도록 exports하겠다.
```

muse

```jsx
var part = require('./mpart.js'); 
console.log(part);
part.f();
```