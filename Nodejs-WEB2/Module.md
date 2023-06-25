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

위 template을 바깥으로 빼준다. (라이브러리를 만든 후 안에 template.js 파일 생성)

```jsx
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
```

```jsx
// main.js
var template = require('./lib/template.js');

// lib/template.js
module.exports = {
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
```