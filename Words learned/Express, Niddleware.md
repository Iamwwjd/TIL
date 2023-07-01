# Express

자체적으로 최소한의 기능을 갖춘 라우팅, 미들웨어 웹 프레임워크이다. 

기본적으로 Express 애플리케이션은 일련의 미들웨어 함수이다.

### **미들웨어 함수 (**Niddleware)

Node.js 애플리케이션에서 요청과 응답 사이에 위치하여 중간 처리를 담당하는 함수이다.

미들웨어는 요청이 서버에 도달하고 응답이 클라이언트로 보내지기 전에 수행되는 작업을 담당한다.

미들웨어는 Express.js 뿐만 아닌 많은 Node.js 앱 프레임워크에서 사용된다.

형태

```jsx
function middleware(req, res, next) {
  // 미들웨어 함수의 로직
}
```

- req (Request) : 요청 객체로 클라이언트로부터의 요청에 대한 정보를 담고있다.
- res (Response) : 응답 객체로 클라이언트로 보낼 응답에 대한 기능과 정보를 담고있다.
- next (Next function) : 다음 미들웨어 함수를 호출하는 함수이다. next() 를 호출하지 않으면 다음 미들웨어 함수로 제어가 넘어가지 않고 요청-응답 주기가 종료된다.
---

### 종류

**body-parser**

웹 애플리케이션에서 HTTP 요청의 본문을 파싱(parse)해서 쉽게 접근할 수 있도록 도와준다. 주로 Express.js와 함께 사용

- JSON 형식의 본문 요청을 해석하여 JavaScript 객체로 변환한다.
- URL-encoded 형식의 요청 본문을 해석하여 JavaScript 객체로 변환한다. → HTML 폼 데이터 전송 시 주 사용
- 멀티파트(form-data) 형식의 요청 본문을 해석하여 파일 업로드 등 바이너리 데이터를 처리한다.

사용 방법

```jsx
// npm을 이용하여 설치
npm install body-parser
```

```jsx
const express = require('express');
const bodyParser = require('body-parser');

const app = express();

app.use(bodyParser.json()); // JSON 형식의 데이터(본문)을 다룰때 사용한다.
app.use(bodyParser.urlencoded({ extended: false })); // URL-encoded (form) 형식의 본문을 다룰때 사용한다.
```

morgan

HTTP 요청에 대한 로깅을 처리한다.

주로 개발 및 디버깅 목적으로 사용, 클라이언트의 요청과 관련된 정보를 로그로 출력하거나 파일에 기록할 수 있다.

사용방법

```jsx
npm install morgan
```

```jsx
const express = require('express');
const morgan = require('morgan');

const app = express();
app.use(morgan('dev')); // 로그를 개발용(dev) 포맷으로 출력

// 미들웨어 등록 후 라우트 및 애플리케이션 로직 작성
```

helmet

다양한 보안 관련 HTTP 헤더를 설정하여 애플리케이션의 보안 수준을 높인다.

기본적인 보안 설정을 제공하여 개발자가 별도의 설정을 수행하지 않아도 안전한 기본구성을 갖ㅊㄹ 수 있다. 

사용방법

```jsx
npm install helmet
```

```jsx
const express = require('express');
const helmet = require('helmet');

const app = express();
app.use(helmet());

// 미들웨어 등록 후 라우트 및 애플리케이션 로직 작성
```

cors(Cross-Origin Resource Sharing)

서로 다른 도메인간의 데이터 공유를 가능하게 해준다. → 웹 애플리케이션에서 다른 도메인 자원에 접근 가능

사용방법

```jsx
npm install cors
```

```jsx
const express = require('express');
const cors = require('cors');

const app = express();
app.use(cors());

// 미들웨어 등록 후 라우트 및 애플리케이션 로직 작성
```

passport

Node.js 기반 앱 애플리케이션에서 인증과 관련된 작업을 처리하기 위한 인증 미들웨어이다.

다양한 인증 전략을 제공하며, 사용자 인증을 간편하게 구현할 수 있도록 도와준다.

사용방법

```jsx
npm install passport
```

모듈 가져오기

```jsx
const passport = require('passport');
const LocalStrategy = require('passport-local').Strategy;
```

사용자 인증 설정

```jsx
passport.use(new LocalStrategy(
  function(username, password, done) {
    // 사용자 인증 로직 구현
  }
));
```

사용자 인증 설정시 세션 저장

```jsx
passport.serializeUser(function(user, done) {
  done(null, user.id);
});

passport.deserializeUser(function(id, done) {
  // 세션에서 사용자 정보 복구
});
```

라우트에서 Passport 사용

```jsx
app.post('/login', passport.authenticate('local', { successRedirect: '/dashboard', failureRedirect: '/login' }));
```


multer

Node.js 기반 웹 애플리케이션에서 파일 업로드를 처리하기 위한 미들웨어다.

클라이언트로부터 전송된 파일을 서버에 저장하거나 다른 처리를 수행하는데 사용된다.

사용방법

```jsx
npm install multer
```

모듈 가져오기

```jsx
const multer = require('multer');
```

Multer 인스턴스 생성

```jsx
const storage = multer.diskStorage({
  destination: function (req, file, cb) {
    // 업로드 파일이 저장될 폴더 경로 지정
    cb(null, 'uploads/');
  },
  filename: function (req, file, cb) {
    // 저장될 파일명 설정
    cb(null, Date.now() + '-' + file.originalname);
  }
});

const upload = multer({ storage: storage });
```

업로드 처리 라우트 설정

```jsx
app.post('/upload', upload.single('file'), (req, res) => {
  // 단일 파일 업로드 처리 로직
  // req.file 객체를 통해 업로드된 파일에 접근 가능
});
```
