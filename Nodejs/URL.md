# URL

=======
![2.png](image/2.png)

![3.png](image/3.png)

main.js를 실행했을때 나오는 각각의 정보들은 n.html과 같은 정적인 파일들을 가져오고 있다. 

→ 만약 1억개의 페이지를 가져온다면 1억개의 정적인 파일이 있어야 한다는 뜻.

그에 반해, 위 웹페이지를 보면 aritcle 라는 서로 같은 파일을 가지고 있음에도 불구하고 뒤쪽 값을 다르게 하는 것을 통해 클라이언트에게 서로 다른 페이지를 만들어 보내고 있다.

![mnews:422.png](image/mnews:422.png)

![mnews:214.png](image/mnews:214.png)

이를 알려면 URL에 형식에 대해 자세히 알아야 하는데 

### [http://opentutorials.org](http://opentutorials.org):3000/main?id-HTML&page=12

위 예시를 나누어 설명해보자면

**http : 프로토콜 통신방식**

사용자가 서버에 접속할 때 어떤 방식으로 접속할것인지에 대한 부분 

[**opentutorials.org](http://opentutorials.org) : host(도메인)**

인터넷에 접속되어 있는 각각의 컴퓨터를 가르키는 주소 

**3000 : port**

한 대의 컴퓨터 안에 여러개의 서버가 있을 수 있는데 이때 클라이언트가 접속했을때 그 중 어떤 서버와 통신했는지 알려준다. 

**main :  path**

컴퓨터의 어떤 디렉토리의 어떤 파일인지 알려준다.

**id-HTML&page=12 : query string**

이를 변경하면 웹서버에게 정보를 전달할 수 있다.

=======
 *query string의 앞은 ? 를 쓰고, 값과 값은 &을 쓰고, 값의 이름과 값은 = 로 구분해야한다.*

이제 query string에 따라 다른 정보를 보여주는 것을 해보겠다

```jsx
var http = require('http');
var fs = require('fs');
var url = require('url');

var app = http.createServer(function (request, response){
    var _url = request.url;
    var queryData  = url.parse(_url, true).query;
		var title = queryData.id;
    console.log(queryData.id);
    if(_url == '/'){
        _url = '/index.html';
    }
    if(_url == '/favicon.ico'){
        return response.writeHead(404);
    }
    response.writeHead(200);
    response.end(queryData.id);
});
app.listen(3000);
```

변수를 만들어 사용하면 편리함과 가독성이 올라간다

위와같은 코드를 적은 후 `localhost:3000`에 접속해주면

![스크린샷 2023-04-27 오후 5.16.08.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/53a796cb-a91f-4b74-bbf9-37ebaa657cb5/%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA_2023-04-27_%E1%84%8B%E1%85%A9%E1%84%92%E1%85%AE_5.16.08.png)

![스크린샷 2023-04-27 오후 5.16.51.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/675b9eb5-f27f-4c3a-bd75-47c1143b41e1/%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA_2023-04-27_%E1%84%8B%E1%85%A9%E1%84%92%E1%85%AE_5.16.51.png)

![스크린샷 2023-04-27 오후 5.26.00.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/22a8f473-9656-403e-b3b0-51270038c323/%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA_2023-04-27_%E1%84%8B%E1%85%A9%E1%84%92%E1%85%AE_5.26.00.png)

query string을 바꿀때마다 페이지가 바뀌면서 페이지에 출력된 정보가 터미널에도 출력된다.

/

위 코드에 

```jsx
var template = `<!doctype html>
<html>
<head>
  <title>${title}</title>
  <meta charset="utf-8">
</head>
<body>
  <h1><a href="../../Downloads/web1_html_internet-master/index.html">WEB</a></h1>
  <ol>
    <li><a href="/?id=HTML">HTML</a></li>
    <li><a href="/?id=CSS">CSS</a></li>
    <li><a href="/?id=JavaScript">JavaScript</a></li>
  </ol>
  <h2>${title}</h2>
  <p><a href="https://www.w3.org/TR/html5/" target="_blank" title="html5 speicification">Hypertext Markup Language (HTML)</a> is the standard markup language for <strong>creating webno pages</strong> and web applications.Web browsers receive HTML documents from a web server or from local storage and render them into multimedia web pages. HTML describes the structure of a web page semantically and originally included cues for the appearance of the document.
  </p><p style="margin-top:45px;">HTML elements are the building blocks of HTML pages. With HTML constructs, images and other objects, such as interactive forms, may be embedded into the rendered page. It provides a means to create structured documents by denoting structural semantics for text such as headings, paragraphs, lists, links, quotes and other items. HTML elements are delineated by tags, written using angle brackets.
  </p>
</body>
</html>
`
    response.end(template);
```
2.HTML 코드를 복붙하고 제목이 있는 곳에 [`queryData.id`](http://queryData.id) 를 넣은 변수를 추가해준다.

이를 실행시키려면 response.end도 [`queryData.id`](http://queryData.id) 가 아닌 변수명인 `template` 을 넣어주어야 한다.

queryData.id 가 각각 HTML, CSS, JavaScript 일때 위 페이지가 나오도록 수정해준다.

처음 들어갔을때 페이지를 index.html이 아닌 “/”로 바꿔주었는데 이를 바꿀때는 위 코드 조건문을

```jsx
 if(_url == '/'){
        title = 'Welcome';
    }
```

이렇게 수정해주어야지 사이트에 접속했을때 Welcome이 뜨게 된다.

이를 실행시키면

![스크린샷 2023-04-27 오후 7.57.52.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/ef1ad931-5678-4116-9fc2-f86b6e061795/%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA_2023-04-27_%E1%84%8B%E1%85%A9%E1%84%92%E1%85%AE_7.57.52.png)

queryData.id값이 제목으로 출력되는 것을 볼 수 있다.

```jsx
<ol>
    <li><a href="/?id=HTML">HTML</a></li>
    <li><a href="/?id=CSS">CSS</a></li>
    <li><a href="/?id=JavaScript">JavaScript</a></li>
  </ol>
```

<ol> 을 <ul>로 바꿔주면 안에 있는 문장들이 순서가 없는 리스트로 변하게 된다.