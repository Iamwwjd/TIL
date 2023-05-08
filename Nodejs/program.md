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

이를 활용하여