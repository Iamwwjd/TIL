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

### 객체_값으로서의 함수

**`OOP` - Object Oriented Programming**

우리가 프로그래밍을 한다 라는 것은 데이터와 데이터를 처리하는것으로 이루어져 있다고 해도 과언이 아니다. 

그리고 우리는 함수를 이용하여 연관되어있는 처리방법들에 이름을 붙여 다른 것들과 구분시킨다.

자바스크립트에서의 함수는 독특한 특성을 가지고 있는데

처리하는 일에 대한 정보를 담고있는 일종의 statement라고 할 수 있으면서 동시에 값을 뜻한다.

```jsx
var i = if(true){console.log('A')} => 오류

var w = while(true){console.log('B')}; => 오류

var f = function (){
    console.log('C');
}
console.log(f);
f(); => 실행 - C 출력
```

이처럼 다른 statment들과 다르게 변수로 값을 지정하고 출력할 수 있다.

```jsx
var f = function (){
    console.log('C');
}
var v = [f]; // 변수로 f를 배열로 지정
v[0](); // v[0]의 값은 f 이기 때문에 함수 실행

var o = {
    func:f // func는 객체의 원소이다. func로 f를 준다.
}
	o.func; // 함수 실행

C
C
```

### 객체_데이터&처리방법을 담는 그릇으로서의 객체

```jsx
var v1 = 'v1';
// 몇 만개의 코드들~~~
v1 = 'egoing' // 누가 v1를 바꿔버린다면~? -> 에러 발생
var v2 = 'v2'
```

함수, 객체를 이용한 해결!

```jsx
var o = { // 폴더라는 기능을 통해 파일들을 정리정돈
    v1:'v1',
    v2:'v2'
}

function f1(){
    console.log(o.v1); //함수에서 o.v1 라는 코드를 처리한다.
}

function f2(){
    console.log(o.v2);
}

f1(); //각 함수가 실행됨
f2();
```

`console.log(o.v1);` 라는 코드에서 `o.` 은 함수가 속해있는 객체가 어떤 이름의 변수에 할당될 것인지 파악하는 의미이다. 

따라서 변수의 이름이 o가 아닌 p로 바뀐다면 함수는 실행되지 않는다. 

함수가 자신이 속해있는 객체를 찾을 수 있게 하려면 `this` 라는 값을 쓰면 된다. 

```jsx
var p = { 
    v1:'v1',
    v2:'v2'
}

function f1(){
    console.log(this.v1); 
}

function f2(){
    console.log(this.v2);
}

p.f1(); //각 함수가 실행됨
p.f2();
```

**함수를 만들때 보통 접두사, 접미사를 통해 함수의 이름을 정한다. 이는 성격이 같은 것들을 그룹핑 하기 위해서이다.**

객체를 통해 그룹핑 하는 방법

```jsx
var template = {
    HTML : function (title, list, body){
        return `
    <!doctype html>
    <html>
    <head>
    <title>WEB1 - ${title}</title>
    <meta charset="utf-8">
    </head>
    <body>
    <h1><a href="/">WEB</a></h1>
    ${list}
    <h3><a href ="/create">create</a></h3>
    ${body}
    </body>
    </html>
    `;
    },
    list : function (filelist){
        var list = '<ul>';

        var i = 0;
        while(i < filelist.length){
            list = list + `<li><a href="/?id=${filelist[i]}">${filelist[i]}</a></li>`;
            i = i+1;
        }

        list = list + '</ul>';
        return list;
    }
}
```

**함수 `templateList`와 `templateHTML` 을 template이라는 객체로 묶었다.**

**사용하는 방법**

```jsx
객체를 사용할때는 

수정 전
var list = templateList(filelist);
var template = templateHTML(title, list, `<h2>${title}</h2>${description}`);

수정 후
var list = template.List(filelist); 가운데에 .을 붙여 사용한다.
var html = template.HTML(title, list, `<h2>${title}</h2>${description}`);
```

모든 코드를 수정해준다.

```jsx
var http = require('http');
var fs = require('fs');
var url = require('url');
var qs = require('querystring')
var template = {
    HTML : function (title, list, body, control){
        return `
    <!doctype html>
    <html>
    <head>
    <title>WEB1 - ${title}</title>
    <meta charset="utf-8">
    </head>
    <body>
    <h1><a href="/">WEB</a></h1>
    ${list}
    ${control}
    ${body}
    </body>
    </html>
    `;
    },
    list : function (filelist){
        var list = '<ul>';
        var i = 0;
        while(i < filelist.length){
            list = list + `<li><a href="/?id=${filelist[i]}">${filelist[i]}</a></li>`;
            i = i+1;
        }

        list = list + '</ul>';
        return list;
    }
}
function templateHTML(title, list, body){
    return `
    <!doctype html>
    <html>
    <head>
    <title>WEB1 - ${title}</title>
    <meta charset="utf-8">
    </head>
    <body>
    <h1><a href="/">WEB</a></h1>
    ${list}
    <h3><a href ="/create">create</a></h3>
    ${body}
    </body>
    </html>
    `;
}

function templateList(filelist){
    var list = '<ul>';

    var i = 0;
    while(i < filelist.length){
        list = list + `<li><a href="/?id=${filelist[i]}">${filelist[i]}</a></li>`;
        i = i+1;
    }

    list = list + '</ul>';
    return list;
}

var app = http.createServer(function(request,response) {
    var _url = request.url;
    var queryData = url.parse(_url, true).query;
    var pathname = url.parse(_url, true).pathname;
    var title = queryData.id;

    if (pathname === '/') { // home 으로 갔냐
        if (queryData.id === undefined) {

            fs.readdir('./data', function (error, filelist) {
                var title = 'Welcome';
                var description = 'Hello Node.js';

                var list = template.list(filelist);
                var html = template.HTML(title, list,
                    `<h2>${title}</h2>${description}`,
                    `<h3><a href ="/create">create</a></h3>`);
                response.writeHead(200);
                response.end(html);
            })


        } else {
            fs.readdir('./data', function (error, filelist) {
                fs.readFile(`data/${queryData.id}`, 'utf8', function (err, description) {
                    var title = queryData.id;
                    var list = template.list(filelist);
                    var html = template.HTML(title, list,
                        `<h2>${title}</h2>${description}`,
                        `<h3><a href ="/create">create</a></h3> 
                                <h3><a href = "/update?id=${title}">update</a></h3>
                                <form action="delete_process" method="post">
                                    <input type="hidden" name="id" value="${title}">
                                    <input type="submit" value="delete">
                                   </form>`);
                    response.writeHead(200);
                    response.end(html);
                });
            });
        }
    } else if(pathname === '/create'){
        fs.readdir('./data', function (error, filelist) {
            var title = 'Web - create';
            var list = template.list(filelist);
            var html = template.HTML(title, list, `
            <form action="/create_process" method="post">
             <p><input type = "text" name = "title" placeholder="title"></p>
             <p><textarea name = "description" placeholder="description"> </textarea></p>

             <p>
                <input type = "submit">
             </p>
            </form>
            `, '');
            response.writeHead(200);
            response.end(html);
        });
    } else if(pathname === '/create_process'){
        var body = '';
        request.on('data', function (data){
            body = body + data;
        });
        request.on('end', function (){
            var post = qs.parse(body);
            var title = post.title;
            var description = post.description;
            fs.writeFile(`data/${title}`, description, 'utf8', function (err){
                response.writeHead(302, {location: `/?id=${title}`});
                response.end('success');
            })
        });
    }else if (pathname === '/update'){
        fs.readdir('./data', function (error, filelist) {
            fs.readFile(`data/${queryData.id}`, 'utf8', function (err, description) {
                var title = queryData.id;
                var list = template.list(filelist);
                var html = template.HTML(title, list, `
                 <form action="/update_process" method="post">
                    <input type="hidden" name="id" value="${title}>"
                    <p><input type = "text" name = "title" placeholder="title" value="${title}"></p>
                    <p><textarea name = "description" 
                    placeholder="description">${description} </textarea>
                    </p>

                     <p>
                        <input type = "submit">
                     </p>
                 </form>
                `,
                    `<h3><a href ="/create">create</a></h3> <h3><a href = "/update?id=${title}">update</a></h3>`);
                response.writeHead(200);
                response.end(html);
            });
        });
    }else if(pathname === '/update_process'){
        var body = '';
        request.on('data', function (data){
            body = body + data;
        });
        request.on('end', function (){
            var post = qs.parse(body);
            var id = post.id;
            var title = post.title;
            var description = post.description;
            fs.rename(`data/${title}`, description, 'utf8', function (err){
                response.writeHead(302, {Location: `/?id=${title}`});
                response.end();
            })
        });
    } else if(pathname === '/delete_process'){
        var body = '';
        request.on('data', function (){
            var post = qs.parse(body);
            var id = post.id;
            fs.unlink(`data/${id}`, function(error){
                response.writeHead(302, {Location:`/`});
                response.end();
            })
        });
    }
    else {
        response.writeHead(404);
        response.end('not found');
    }
});

app.listen(3000);
```