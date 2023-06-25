# program
프로그램은 크게 입력을 받아 정보를 처리한 후 그 결과를 출력하는 기계라고 말할 수 있다.

Parameter : 형식이 있는 입력되는 정보

Argument : 형식에 맞게 실제로 입력되는 값

이제 조건문을 활용하여 만들어 놓았던 main.js 를 더 쓸모있게 만들어보겠다.

이제 사용자가 qrerystring이 없는 값으로 들어왔을때는 Helloword를 출력하고

아래 목록을 선택하였을때는 id값에 해당되는 파일을 찾아 형성하고

그 외의 주소로 들어왔을때는 오류메세지를 전송하는 기능을 만들것이다.

그렇기 하기 위해 제일 먼저 봐야할것은 사용자가 `root` 로 접근한지를 구분해야 한다.

여기서 root라 함은 주소 뒤에 정보가 붙지 않는 ex)[http://localhost:3000](http://localhost:3000/) 을 뜻한다.

그렇다면 먼저 queryData 라는 변수에 어떤 내용이 담겨있는지부터 알아보자.

```jsx
var queryData = myURL.searchParams.get('id');
console.log(url.parse(_url,true));
```

main.js 를 실행하면

```jsx
Url {
  protocol: null,
  slashes: null,
  auth: null,
  host: null,
  port: null,
  hostname: null,
  hash: null,
  search: null,
  query: [Object: null prototype] {},
  pathname: '/',
  path: '/',
  href: '/'
}
```

위와 같이

즉 `console.log(url.parse(_url,true));`는 주어진 URL 정보를 분석하여 우리가 쉽게 쓸 수 있도록 도와주는 코드이다.

여기서 path는 querystring이 포함되어 있고 pathname은 querystring이 포함되어 있지 않은 path이다.

우리는 pathname이 필요하기 때문에 `var pahtname = url.parse(_url,true).pathname;`을 넣어준다.

이를 활용하여 아래 조건문을 작성해준다.

```jsx
if (pahtname === '/') {
      fs.readFile(`data/${queryData.id}`, 'utf8', function (err, description) {
          var template = ` <!doctype html>
<html>
<head>
  <title>WEB1 - ${title}</title>
  <meta charset="utf-8">
</head>
<body>
  <h1><a href="/">WEB</a></h1>
  <ul>
    <li><a href="/?id=HTML">HTML</a></li>
    <li><a href="/?id=CSS">CSS</a></li>
    <li><a href="/?id=JavaScript">JavaScript</a></li>
  </ul>
  <h2>${title}</h2>
  <p>${description}</p>
</body>
</html>
 `;
          response.writeHead(200);
          response.end(template);
      })
  } else {
      response.writeHead(404);
      response.end('not found'); // 파일을 찾을 수 없다
  }
```

현 접속이 path가 없는 경로로 접속했다면 if 안에 있는 코드를 실행하고

<<<<<<< HEAD
그 외(else)로 접속을 했다면 error를 띄워준다.

```jsx
var http = require('http');
var fs = require('fs');
var url = require('url');

var app = http.createServer(function(request,response) {
    var _url = request.url;
    var queryData = url.parse(_url, true).query;
    var pathname = url.parse(_url, true).pathname;
    var title = queryData.id;

    if (pathname === '/') {
        if (queryData.id === undefined) {
            fs.readFile(`data/${queryData.id}`, 'utf8', function (err, description) {
                var template = `<!doctype html>
<html>
<head>
  <title>WEB1 - ${title}</title>
  <meta charset="utf-8">
</head>
<body>
  <h1><a href="/">WEB</a></h1>
  <ul>
    <li><a href="/?id=HTML">HTML</a></li>
    <li><a href="/?id=CSS">CSS</a></li>
    <li><a href="/?id=JavaScript">JavaScript</a></li>
  </ul>
  <h2>${title}</h2>
  <p>${description}</p>
</body>
</html>
 `;
                response.writeHead(200);
                response.end(template);
            });
        } else {
            fs.readFile(`data/${queryData.id}`, 'utf8', function (err, description) {
                var template = `<!doctype html>
<html>
<head>
  <title>WEB1 - ${title}</title>
  <meta charset="utf-8">
</head>
<body>
  <h1><a href="/">WEB</a></h1>
  <ul>
    <li><a href="/?id=HTML">HTML</a></li>
    <li><a href="/?id=CSS">CSS</a></li>
    <li><a href="/?id=JavaScript">JavaScript</a></li>
  </ul>
  <h2>${title}</h2>
  <p>${description}</p>
</body>
</html>
 `;
                response.writeHead(200);
                response.end(template);
            });
        }
    } else {
        response.writeHead(404);
        response.end('not found');
    }
});

app.listen(3000);
```

조건문을 사용한 웹 페이지 구현을 알아보았다. 

undefined = 정의되지 않은 데이터 키워드.
=======
그 외(else)로 접속을 했다면 error를 띄워준다.
>>>>>>> 291b8edc765ea3da3d84d63ecbba8bdd416d8f07

### 파일목록 알아내기

**fs.readdir**

```jsx
const testFolder = './tests/';
const fs = require('fs') // const는 아직 안배웠으니 var로 변경해서 사용

fs.readdir (testFolder, (err, files) => {
	files.forEach(file => {
		console.log(file);
	});
}) // 이건 예제이고 필요없는 부분은 잘라서 사용
```

readdir.js file을 만들어 아래 코드를 적어준다

```jsx
var testFolder = './data'; 
var fs = require('fs')

fs.readdir (testFolder, function (error,filelist){
    console.log(filelist)
})
```

이를 실행하면 data에 있는 파일의 목록을 배열로 만들어서 내놓는다.

### 글 목록 출력하기

```jsx
<ul>
    <li><a href="/?id=HTML">HTML</a></li>
    <li><a href="/?id=CSS">CSS</a></li>
    <li><a href="/?id=JavaScript">JavaScript</a></li>
  </ul>
```

위 코드를 파일 목록으로 바꾸어 보겠다.

```jsx
var title = 'Welcome';
                var discription = 'Hello Node.js';
                var template = `<!doctype html>
<html>
<head>
  <title>WEB1 - ${title}</title>
  <meta charset="utf-8">
</head>
<body>
  <h1><a href="/">WEB</a></h1>
  <ul>
    <li><a href="/?id=HTML">HTML</a></li>
    <li><a href="/?id=CSS">CSS</a></li>
    <li><a href="/?id=JavaScript">JavaScript</a></li>
  </ul>
  <h2>${title}</h2>
  <p>${description}</p>
</body>
</html>
 `;
                response.writeHead(200);
                response.end(template);
```

이 코드를 파일 목록을 가져오는 코드로 감싸준다

```jsx
var fs = require('fs');

fs.readdir('./data', function (error, filelist){
            console.log(filelist);
        })
```

이를 실행하면 data 폴더에 있는 파일 `[ 'CSS', 'HTML', 'JavaScript']` 이 출력된다.

이를 붙여넣기 하고 <ul> 코드를 삭제 한 후 변수인 `list` 로 바꿔준다 

그리고 위 쪽에 list 변수를 만들어준다.

`list`

```jsx
var list = '<ul>';

            var i = 0; // 변수 지정
            while(i < filelist.length){ // i가 filelist의 length보다 작을때까지
                list = list + '<li>${filelist[i]}</li>'; // list 증가d
                i = i+1; // i 증가
            }

list = list + '</ul>'; // list의 시작과 끝은 <ul> 이다.
```

이걸 실행시킨다면 파일의 목록이 출력 될 것이다. 

```jsx
var list = '<ul>';

            var i = 0;
            while(i < filelist.length){
                list = list + '<li><a href = "/?id=${filelist[i]}" >${filelist[i]}</a></li>';
                i = i+1;
            }

            list = list + '</ul>';
            var template = `<!doctype html>
```

<a> 태그를 사용해 링크를 걸어준다.

main.js 에서 else 아래에 있는 코드는 id 값이 있을 때 실행 되는 코드이기 때문에 위 코드를 copy 해서 똑같이 적용시켜 준다.

글을 쓸 수 있는 경로로 가는 링크 만들기

`templateHTML` 함수에

```jsx
<h3><a href ="/create">create</a><h3> // create를 누르면 create 페이지로 넘어감
```

if 에 있는 아래 코드를

```jsx
fs.readdir('./data', function (error, filelist) {
                var title = 'Welcome';
                var description = 'Hello Node.js';

                var list = templateList(filelist);
                var template = templateHTML(title, list, `<h2>${title}</h2>${description}`);
                response.writeHead(200);
                response.end(template);
            })
```

아래쪽에 else if를 만들어 넣어준다.

```jsx
else if(pathname === '/create'){
        fs.readdir('./data', function (error, filelist) {
            var title = 'Web - create';
            var list = templateList(filelist);
            var template = templateHTML(title, list, `
            <form action="http://localhost:3000/create_process" method="post">
             <p><input type = "text" name = "title" placeholder="title"></p>
             <p><textarea name = "description" placeholder="description"> </textarea></p>

             <p>
                <input type = "submit">
             </p>
            </form>
            `);
            response.writeHead(200);
            response.end(template);
        })
```

`placeholder` 는 사용자가 어떤 입력값을 적어야하는지 알려주는 용도로 사용한다.

`refactoring` 동작방법은 똑같이 유지하면서  내부 코드는 효율적으로 바꾸는 것

사용자가 form으로 정보를 전송할때 post 방식으로 전달함 → 이 데이터를 node.js안에서 가져오기 위해서는?

```jsx
requst.on() 사용 이유
웹브라우저가 post방식으로 데이터를 전송할때 많은 데이터를 처리하다 무리가 가는 문제점이 생긴다. -> 전송 되는 데이터가 많을때를 대비하여 일정량의 데이터를 수신할때마다 callback함수를 호출한다.

request.on('data', function (data){
            body = body + data;
        }); // bodydata에 callback이 실행될때마다 data를 추가해준다. 

정보가 들어오다가 들어올 정보가 없으면 `request.on('end', function)`에 해당되는 callback이 실행될때 정보 수신이 끝났다고 생각한다.

코드 윗줄에
var qs = require('querystring') 를 추가해주고
request.on('end', function (){
   var post = qs.parse(body); // post data의 post data가 들어있을 것
});

console.log(post.title); -> tilte의 값이 node.js가 됨
console.log(post.description) -> 본문이 된다.
```

완성코드

```jsx
else if(pathname === '/create_process'){
        var body = '';
        request.on('data', function (data){
            body = body + data;
        });
        request.on('end', function (){
            var post = qs.parse(body);
            var title = post.title;
            var description = post.description;
            console.log(post.title);
        });
        response.writeHead(200);
        response.end('success');
    } // 실행을 하면 node가 콘솔창에 뜸
```

```jsx
301 - 위 주소로 영원히 바뀜 -> 앞으로는 위 주소로 오라는 뜻
200 - 성공
302 - 페이지를 다른곳으로 이동시키는 뜻

response.writeHead(302, {location: `/?id=${title}`}); //페이지가 잘 넘어간다.
```

---

`create` 버튼 옆에 `update` 버튼을 만들어준다.

```jsx
${list}
    <h3><a href ="/create">create</a></h3> <h3><a href = "/update">update</a></h3> // create
${body}
```

각 if문의 html 변수에 control을 추가해준다.

`if (pathname === '/')` (홈) 

```jsx
var html = template.HTML(title, list,
                    `<h2>${title}</h2>${description}`, 
                    `<h3><a href ="/create">create</a></h3>`);
```

`else` (id값 선택)

```jsx
var html = template.HTML(title, list, 
							`<h2>${title}</h2>${description}`,
              `<h3><a href ="/create">create</a></h3> <h3><a href = "/update?id=${title}">update</a></h3>`);
```

---

수정할 정보 전송

update page 기능 구현

```jsx
else if (pathname === '/update'){
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
}
```

---

삭제버튼 구현

```jsx
else {
            fs.readdir('./data', function (error, filelist)
.
.
.
					<form action="delete_process" method="post"> // 반드시 post방식으로 보낸다.
                            <input type="hidden" name="id" value="${title}"> // gidden -> 보이지않게
                            <input type="submit" value="delete">
                            </form>`);
```

프로그램에서 update 버튼을 누르면 update page로 이동하지만,  delete 버튼을 눌렀을때는 

페이지 이동을 하지 않고 바로 삭제한다.→ 삭제버튼을 링크로 만들면 안된다. → form으로 만든다.

```jsx
else if(pathname === '/delete_process'){
        var body = '';
        request.on('data', function (data) {
            body = body + data;
        });
        request.on('end', function(){
            var post = qs.parse(body);
            var id = post.id;
            fs.unlink(`data/${id}`, function(error){
                response.writeHead(302, {Location:`/`});
                response.end();
            })
        });
    }
```