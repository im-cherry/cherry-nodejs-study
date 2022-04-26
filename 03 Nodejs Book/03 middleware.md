# 03 middleware

## 1. 미들웨어

- 미들웨어에는 인증수행, 예외처리, 세션처리, 라우터 등 많은 종류가 있습니다.
- 미들웨어는 `app.use()` 메서드를 통해 사용합니다.

<br/>
<br/>

## 2. express로 서버 만드는 방법

1. express를 불러옵니다.
2. 포트를 설정해줍니다.
3. 공통적으로 사용하는 미들웨어를 장착해줍니다.
4. 라우터를 구성합니다.
5. 404 처리 미들웨어를 구성합니다.
6. 오류 처리 미들웨어를 구성합니다.
7. 생성된 서버가 포트를 리스닝합니다.

```
$ npm install morgan cookie-parser express-session
```

```javascript
// 1. express 불러오기
const express = require("express");
const app = express();

// 2. 포트 설정
app.set("port", process.env.PORT || 8080);

// 3. 공통적으로 사용하는 미들웨어
app.use(express.static(__dirname + "/public"));

// 4. 라우터 구성
app.get("/", (req, res) => {
  const output = `
    <h2>express 로 웹 만들기</h2><br>
    <p>메인 페이지입니다.</p>
    <img src="./sample.png" alt="express 로고" />
    `;
  res.send(output);
});

app.get("/user/:id", (req, res) => {
  res.send(req.params.id + " 님의 개인 페이지 입니다.");
});

// 5. 404 처리 미들웨어
app.use(function (req, res, next) {
  res.status(404).send("Sorry can't find that!");
});

// 6. 오류 처리 미들웨어
app.use(function (err, req, res, next) {
  console.error(err.stack);
  res.status(500).send("Something broke!");
});

// 7. 서버 리스닝
app.listen(app.get("port"), () => {
  console.log(app.get("port"), " 포트에서 서버 실행중...");
});
```

> 응답을 위한 함수
>
> res.send() : 문자열로 응답  
> res.json() : json 객체로 응답  
> res.sendFile() : 파일로 응답

<br/>
<br/>

## 3. 쿠키 전달

<br/>
<br/>
