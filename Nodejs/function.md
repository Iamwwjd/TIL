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

### 함수의 출력

직접 만든 함수는 console.log를 통해 화면에 출력되는게 전부이지만,

내장함수는 console.log 외에도 (filwrite(’result.txt’, Math.round());등을 활용해 파일에 출력할 수도 있고,

email()를 활용하는 등 여러 방도로 사용할 수 있다.

직접 만든 함수를 여러 방도로 사용하려면 return을 써주어야 한다.

```jsx
sum(5,7);

function sum(first, second){ 
    return (first + second) // 함수의 값을 리턴하며 값을 12로 만듦
}

console.log(sum(5,7)); //12
```

```jsx
function sum(first, second){ 
		console.log('a');
    return (first + second) // 함수의 값을 리턴하며 값을 12로 만듦
		console.log('b'); // 리턴이 되면 그 즉시 함수의 계산이 끝나기 때문에 실행이 안된다.
}
```

### 함수를 이용한 정리

코드가 많아지면 코드가 복잡해지며 관리가 힘들어지고 가독성이 낮아진다.

main.js에서 중복되는 부분의 코드를 함수로 만들어준다.

```jsx
function templateHTML(){
    return `<!doctype html>

    <html>
    <head>
    <title>WEB1 - ${title}</title>
    <meta charset="utf-8">
    </head>
    <body>
    <h1><a href="/">WEB</a></h1>
    ${list}
    ${body} // <h2>${title}</h2>${discription}을 ${}로 묶어준다.
    </body>
</html>
    `;
}

var template = templateHTML(title, list, `<h2>${title}</h2>${discription}`);
```

또 중복되는 부분이 없는지 확인하고 함수로 만들어준다.

```jsx
function templateList(filelist){
    var list = '<ul>';

    var i = 0;
    while(i < filelist.length){
        list = list + `<li><a ' +
                    'href ="/?id=${filelist[i]}">${filelist[i]}</a></li>`;
        i = i+1;
    }

    list = list + '</ul>';

    return list;
}

var list = templateList(filelist);
```