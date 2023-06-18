# Security

현재 main.js에서는

```jsx
fs.readdir('./data', function (error, filelist) {
                fs.readFile(`data/${queryData.id}`, 'utf8', function (err, description) {
```

주소를 (queryData.id)로 받아오기 때문에 보안방면에서 취약한 부분이 있다.

예를 들어 내가 password.js라는 파일에 나의 패스워드를 넣어놓은 후 

누군가가  `/?id=../password.js` 이라는 주소로 페이지에 접근한다면 password.js에 있는 나의 패스워드는 공개가 될 것이다.