# 05 HTTP Module

## 1. The Build-in HTTP Module

Node.js 에는 HTTP 라는 내장 모듈이 있어 Node.js가 HTTP(HyperText Transfer Protocol)를 통해 데이터를 전송할 수 있습니다.

```javascript
var http = require("http");
```

<br/>
<br/>

## 2. Node.js as a WebServer

HTTP 모듈은 서버 포트를 수신 대기하고 클라이언트에 응답을 제공하는 HTTP 서버를 생성할 수 있습니다.  
`createServer` 메서드를 사용하여 HTTP 서버를 만듭니다.

```javascript
var http = require("http");

http
  .createServer(function (req, res) {
    res.write("Hello World!"); // 클라이언트에 응답 write
    res.end(); // 응답 종료
  })
  .listen(8080); // 누군가 포트 8080에 액세스하려고 할 때 실행됩니다.
```

<br/>
<br/>

## 3. Add an HTTP Header

HTTP 서버의 응답이 HTML로 표시되어야 하는 경우 올바른 컨텐츠 유형의 HTTP 헤더를 포함해야 합니다.

`res.writeHead(상태 코드, 응답 헤더)`

```javascript
var http = require("http");
http
  .createServer(function (req, res) {
    res.writeHead(200, { "Content-Type": "text/html" });
    res.write("Hello World!");
    res.end();
  })
  .listen(8080);
```

<br/>
<br/>

## 4. Read the Query String

`createServer(res, req)` 함수에서 `req` 객체는 도메인 이름 뒤에 오는 URL 부분을 포함하는 `url` 이라는 속성이 있습니다.

```javascript
var http = require("http");

http
  .createServer(function (req, res) {
    res.writeHead(200, { "Content-Type": "text/html" });
    rew.write(req.url);
    res.end();
  })
  .listen(8080);
```

`https://localhost:8080/summer` 으로 접속한 경우 `/summer` 가 화면에 표시됩니다.

<br/>
<br/>

## 5. Split the Query String

쿼리 문자열을 URL 모듈과 같이 읽을 수 있는 부분으로 쉽게 분할할 수 있는 내장 모듈 `url`이 있습니다.

```javascript
var http = require("http");
var url = require("url");

http
  .createServer(function (req, res) {
    res.writeHead(200, { "Content-Type": "text/html" });
    var q = url.parse(req.url, true).query;
    var txt = q.year + " " + q.month;
    res.end(txt);
  })
  .listen(8080);
```

`https://localhost:8080/year=2017&month=July` 으로 접속한 경우 `2017 July` 가 화면에 표시됩니다.

<br/>
<br/>

:arrow_forward:[06 File System](./06%20File%20System.md) :arrow_forward:
