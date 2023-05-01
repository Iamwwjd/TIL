# CRUD

정보시스템의 핵심적인 매커니즘을 CRUD라고 많이 부르는데, 

여기서 CRUD는 Create Read Update Delete 의 약자이다.

`cd : 디렉토리를 변경하는 명령어`

node.js를 사용하여 파일을 읽어보겠다. 

전에 만들어두었던 예제들을 사용하여

1.html, 2.html, 3.html에 <p>안에 있는 내용들만 파일을 새로 생성하여 옮겨준다.

```jsx
## 1.html

<a href="https://www.w3.org/TR/html5/" target="_blank" title="html5 speicification">Hypertext Markup Language (HTML)</a> is the standard markup language for <strong>creating webno pages</strong> and web applications.Web browsers receive HTML documents from a web server or from local storage and render them into multimedia web pages. HTML describes the structure of a web page semantically and originally included cues for the appearance of the document.
  </p><p style="margin-top:45px;">HTML elements are the building blocks of HTML pages. With HTML constructs, images and other objects, such as interactive forms, may be embedded into the rendered page. It provides a means to create structured documents by denoting structural semantics for text such as headings, paragraphs, lists, links, quotes and other items. HTML elements are delineated by tags, written using angle brackets.
```

```jsx
## 2.html

Cascading Style Sheets (CSS) is a style sheet language used for describing the presentation of a document written in a markup language. Although most often used to set the visual style of web pages and user interfaces written in HTML and XHTML, the language can be applied to any XML document, including plain XML, SVG and XUL, and is applicable to rendering in speech, or on other media. Along with HTML and JavaScript, CSS is a cornerstone technology used by most websites to create visually engaging webpages, user interfaces for web applications, and user interfaces for many mobile applications.
```

```jsx
## 3.html

JavaScript (/ˈdʒɑːvəˌskrɪpt/[6]), often abbreviated as JS, is a high-level, dynamic, weakly typed, prototype-based, multi-paradigm, and interpreted programming language. Alongside HTML and CSS, JavaScript is one of the three core technologies of World Wide Web content production. It is used to make webpages interactive and provide online programs, including video games. The majority of websites employ it, and all modern web browsers support it without the need for plug-ins by means of a built-in JavaScript engine. Each of the many JavaScript engines represent a different implementation of JavaScript, all based on the ECMAScript specification, with some engines not supporting the spec fully, and with many engines supporting additional features beyond ECMA.
```

그리고 main.js에 

```jsx
fs.readFile(`data/${queryData.id}`), 'utf8', function(err, data){
					
}
```

위 파일을 만들어주고 저번에 만들어놨던 template 변수 내용을 잘라서 중괄호 안에 넣어준다.

그리고 template의 <p>안에 있는 내용을 ${discription} 변수로 바꿔주고 실행해보면 정상적으로 실행이 된다.