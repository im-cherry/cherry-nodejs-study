# 07 Express로 웹 서버 구축하기

## 1. Express.js 로 웹 서버 만들기

익스프레스는 Node.js 에서 웹 애플리케이션 혹은 API 서버를 구축하는데 가장 많이 사용되는 대표적은 프레임워크 입니다.

- package.json 파일 생성

  ```
  $ npm init
  ```

  ```json
  {
    "name": "node-project",
    "version": "1.0.0",
    "description": "This package is for learning node.js",
    "main": "index.js",
    "scripts": {
      "test": "echo \"Error: no test specified\" && exit 1"
    },
    "keywords": ["node", "express", "mysql"],
    "author": "Seungwon Go",
    "license": "ISC"
  }
  ```

- Express 설치

  ```
  $ npm install express
  ```

- app.js 생성

  ```javascript
  const express = require("express");
  const app = express();
  const port = 3000; // 서버 포트 번호

  // 클라이언트에서 HTTP 요청 메서드 중 GET을 이용해서 'host:port'로 요청을 보내면 실행되는 라우트 입니다.
  app.get("/", (req, res) => {
    res.send("Hello World!");
  });

  // app.listen() 함수를 사용해서 서버를 실행합니다.
  app.listen(port, () => {
    console.log(`서버가 실행됩니다. http://localhost:${port}`);
  });
  ```

  ```
  $ node app.js
  ```

<br/>
<br/>

## 2. 라우팅 처리하기

- 라우팅은 특정 엔드 포인트에 대한 클라이언트 요청에 애플리케이션이 응답하는 방법을 결정하는 것을 말합니다.

  > `app.METHOD(PATH, HANDLER)`
  >
  > app : express 의 인스턴스
  > METHOD : HTTP 요청 메서드
  > PATH : 서버에서의 경로
  > HANDLER : 라우트가 일치할 때 실행되는 함수

  ```javascript
  const express = require("express");
  const app = express();

  app.listen(3000, () => {
    console.log("3000번 포트로 웹 서버 실행!");
  });

  app.get("/customer", function (req, res) {
    res.send("get 요청에 대한 응답!");
  });

  app.post("/customer", function (req, res) {
    res.send("post 요청에 대한 응답!");
  });
  ```

- `route` 메서드를 이용하면 get, post, put 과 같은 라우트 메소드를 한 곳에 작성할 수 있습니다.

```javascript
const express = require("express");
const app = express();

app.listen(3000, () => {
  console.log("3000번 포트로 웹 서버 실행!");
});

app
  .route("/customer")
  .get(function (req, res) {
    res.send("고객 정보 조회");
  })
  .post(function (req, res) {
    res.send("신규 고객 추가");
  })
  .put(function (req, res) {
    res.send("고객 정보 수정");
  })
  .delete(function (req, res) {
    res.send("고객 정보 삭제");
  });
```

- Router 클래스를 사용하면 라우트 처리를 하나의 파일에서 하는 것이 아니라 여러 개의 파일로 분리해서 각각의 기능에 맞게 구현할수 있습니다.

  - node-project/blob/main/routes/customer.js

    ```javascript
    const express = require("express");
    const router = express.Router();

    // app.js 에서 기본 경로에 /customer 를 사용하기 때문에 /customer 라우트 경로를 가짐

    // 고객 정보 조회를 위한 라우트 : /customer
    router.get("/", function (req, res) {
      res.send("customer 라우트");
    });

    // 고객 정보 추가를 위한 라우트 : /customer/insert
    router.post("/insert", function (req, res) {
      res.send("customer/insert 라우트");
    });

    // 고객 정보 수정을 위한 라우트 : /customer/update
    router.put("/update", function (req, res) {
      res.send("customer/update 라우트");
    });

    // 고객 정보 삭제를 위한 라우트 : /customer/delete
    router.delete("delete", function (req, res) {
      res.send("customer/delete 라우트");
    });

    module.exports = router;
    ```

- node-project/blob/main/app.js

  ```javascript
  const express = require("express");
  const app = express();

  const customerRoute = require("./routes/customer");

  app.use(
    express.json({
      limit: "50mb", // 최대 50메가
    })
  ); // 클라이언트 요청 body를 json으로 파싱 처리

  app.listen(3000, () => {
    console.log("3000번 포트로 웹 서버 실행");
  });

  app.use("/customer", customerRoute);
  ```

<br/>
<br/>

## 3. Express 에서 에러 처리하기

익스프레스에는 앱에서 발생할 수 있는 모든 에러를 처리하는 에러 핸들러가 내장되어 있습니다.

```javascript
app.get("");
```

<br/>
<br/>

## 4. Express 에서 정적 파일 제공하기

<br/>
<br/>

## 5. 미들웨어 모듈

익스프레스는 웹 서버 운영을 위해 다양한 미들웨어 모듈을 제공합니다.  
미들웨어 모듈은 요청과 응답의 중간에서 목적에 맞는 특정 기능을 하는 함수입니다.

- cookie-session : 쿠기 기반의 세션 관리 미들웨어

  ```
  $ npm install cookie-session
  ```

  ```javascript
  const cookieSession = require("cookie-session");
  const express = require("express");
  const app = express();

  app.use(
    cookieSession({
      name: "session",
      keys: [],
      maxAge: 24 * 60 * 60 * 1000, // 24시간 유지
    })
  );
  ```

- express-session : 서버 기반의 세션을 생성

  ```
  $ npm install express-session
  ```

  ```
  $ npm install session-file-store  # 세션 정보를 파일로 저장해서 관리 가능
  ```

  ```javascript
  const session = require("express-session");
  // const fileStore = require("session-file-store")(session);
  const express = require("express");
  const app = express();

  app.use(
    session({
      secret: "secret key", // 암호화 하는데 쓰일 키
      resave: false, // 세션에 변경 사항이 없어도 항상 다시 저장할지 여부
      saveUninitialized: true, // 초기화되지 않은 세션을 스토어(저장소)에 강제로 저장할지 여부
      cookie: {
        // 세션 쿠기 설정(세션 관리 시 클라이언트에 보내는 쿠키)
        httpOnly: true, // true이면 클라이언트 자바스크립트에서 document.cookie 로 쿠키 정보를 볼 수 없음
        secure: true, // true 이면 https 환경에서만 쿠키 정모를 주고 받도록 처리
        maxAge: 60000, // 쿠키가 유지되는 시간(ms)
      },
      // store : new fileStore()  // 세션 저장소로 fileStore 사용
    })
  );

  app.listen(3000, () => {
    console.log("3000번 포트로 서버를 실행했습니다.");
  });

  // 로그인 요청 시 사용자 정보 확인 후 세션에 사용자 정보 저장
  app.post("/login", (req, res, next) => {
    const { email, pw } = req.body.param;

    req.session.email = email;
    req.session.is_logined = true;

    // 세션 저장
    req.session.save((err) => {
      if (err) throw err;
      res.redirect("/home"); // 로그인 후 홈화면 이동
    });
  });

  // 로그아웃 요청시 세션 삭제 후 로그인 페이지로 이동
  app.post("logout", (req, res, next) => {
    req.session.destroy(); // 세션 삭제
    res.redirect("/login"); // 로그인 페이지 이동
  });
  ```

- cors : 쿠키 기반의 세션을 생성

  CORS(Cross-Origin Resource Sharing) 는 추가 HTTP 헤더를 사용해서 도메인 또는 포트가 다른 서버의 자원에 접근할 수 있는 권한을 부여하도록 브라우저에 알려주는 체제를 말합니다.  
  `cors` 는 도메인과 포트를 지정해서 권한이 있는 클라이언트만 접근할 수 있도록 접근 권한을 부여하고 관리할 수 있는 미들웨어 입니다.

  ```
  $ npm install cors
  ```

  ```javascript
  const cores = require("cors");
  const express = require("express");
  const app = express();

  const corsOptions = {
    origin: "http://example.com", // 허용할 도메인 설정
    optionsSuccessStatus: 200,
  };

  app.use(cors(corsOptions)); // cors를 모든 라우터에 적용

  app.get("/products/:id", function (req, res, next) {
    res.json({ msg: "This is CORS-enabled for all origins!" });
  });

  app.listen(80, function () {
    console.log("80번 포트로 서버를 실행했습니다.");
  });
  ```

- multer : multi-part 폼 데이터 처리

  multer 은 multi-part/form-data 데이터를 처리하기 위한 미들웨어 입니다.

  ```
  $ npm install multer
  ```

  ```javascript
  const multer = require("multer");
  const path = require("path");
  const express = require("express");
  const app = express();

  app.listen(3000, () => {
    console.log("3000번 포트로 서버를 실행했습니다.");
  });

  const storage = multer.diskStorage({
    // 디스크 저장소 정의
    destination: function (req, file, cb) {
      cb(null, "uploads/"); // 전송된 파일 저장 디렉토리 설정
    },
    filename: function (req, file, cb) {
      // cb(null, file.originalname)  // 전송된 파일 이름 설정
      cb(null, newDate().valueOf() + path.extname(file.originalname)); // 시스템 시간으로 파일 이름 설정
    },
  });
  const upload = multer({ storage: storage });

  app.post("/profile", upload.single("avatar"), function (req, res, next) {
    console.log(req.file); // avatar 이름의 싱글 파일
    console.log(req.body); // 일반적인 ㅍ모 데이터
  });

  app.post(
    "/photos/upload",
    upload.array("photos", 12),
    function (req, res, next) {
      console.log(req.files); // photos 이름의 멀티 파일
    }
  );
  ```

<br/>
<br/>

## 6. Postman 설치 및 익스프레스 라우트 테스트

- Postman을 사용하면 구현한 서버 프로그램을 테스트할 수 있습니다.

- [공식 홈페이지](https://postman.com/download) 에서 설치 파일을 다운로드하여 설치합니다.

- Postman 을 이용해 익스프레스 라우트 테스트 해보기

  - Collection > 생성 버튼(+) > Nex Collection의 더보기 버튼 > Rename 클릭
  - Collection 이름 : 'Express 라우트 테스트'
  - Express 라우트 테스트의 더보기 버튼 > Add request 클릭
  - HTTP 요청 메소드와 요청 URL 입력 후, Send 버튼 클릭

  ```javascript
  app.get("/", function (req, res) {
    res.send("Hello World!");
  });

  app.get("/about", function (req, res) {
    res.send("about");
  });

  app.post("/customer", function (req, res) {
    console.log(req.body.param);
    res.send(req.body.param);
  });
  ```

<br/>
<br/>

:arrow_forward:[08 데이터 베이스 사용하기](./08%20%EB%8D%B0%EC%9D%B4%ED%84%B0%20%EB%B2%A0%EC%9D%B4%EC%8A%A4%20%EC%82%AC%EC%9A%A9%ED%95%98%EA%B8%B0.md):arrow_forward:
