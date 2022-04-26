# 01 http

## 1. 프로젝트 설정하기

```
$ npm init
```

<br/>
<br/>

## 2. 웹 페이지의 요청에 대한 응답

```javascript
const http = require("http");

http
  .createServer((req, res) => {
    res.writeHead(200, { "Content-Type": "text/html; charset=utf-8" });
    res.write("<h1>Node.js 로 서버 만들기</h1>");
    res.end("<p>http 모듈을 공부중입니다.</p>");
  })
  .listen(8080, () => {
    console.log("8080 포트에서 서버 연결 중...");
  });
```

- `createServer(콜백함수(요청, 응답))` : 서버를 만드는 함수
- `res.writeHead(요청코드, 콘텐츠 타입)` : 응답에 대한 정보(헤더)를 기록하는 함수
- `res.write(클라이언트에 보낼 데이터)` : 응답에 대한 데이터를 보내는 함수
- `res.end(클라이언트에 보낼 데이터)` : 응답을 종료하는 메서드
- `.listen(클라이언트와 연결한 포트번호, 콜백함수)` : 서버가 연결되면 콜백함수 실행

<br/>
<br/>

## 3. 파일을 보내는 응답 코드

```javascript
const http = require("http");
const fs = require("fs").promise();

http
  .createServer(async (req, res) => {
    try {
      const f = await fs.readFile("./fs_text.html");
      res.writeHead(200, { "Content-Type": "text.html; charset=utf-8" });
      res.end(f);
    } catch (err) {
      console.error(err);
      res.writeHead(500, { "Content-Type": "text.html; charset=utf-8" });
      res.end(err.message);
    }
  })
  .listen(8080, () => {
    console.log("8080 포트에서 서버 연결중...");
  });
```

<br/>
<br/>

## 4. REST를 통한 페이지 생성

```javascript
const http = require("http");

http
  .createSever((req, res) => {
    if (req.url === "/") {
      res.write("Hello");
      res.end();
    }
  })
  .listen(8080, () => {
    console.log("8080 포트에서 서버 연결");
  });
```

- req.url : localhost:8080 뒤의 주소

<br/>
<br/>

:arrow_forward:[02 express](./02%20express.md):arrow_forward:
