# 03 Get Started

## 1. Download Node.js

[Node.js 공식 웹사이트](https://nodejs.org/en/) 에서 다운로드 합니다.

<br/>
<br/>

## 2. Getting Started

Node.js 를 다운로드하여 설치했으면 웹 브라우저에 "Hello World"를 표시해 보겠습니다.

- myfirst.js

  ```javascript
  var http = require("http");

  http
    .createServer(function (req, res) {
      res.writeHead(200, { "Content-Type": "text/html" });
      res.end("Hello World!");
    })
    .listen(8080);
  ```

<br/>
<br/>

## 3. Command Line Interface

Node.js 파일은 Command Line Interface 프로그램에서 시작합니다.

<br/>
<br/>

## 4. Initiate the Node.js File

Command Line Interface 에 아래 명령어를 입력합니다.

```
$ node myfirst.js
```

이제 컴퓨터가 서버로 동작합니다.  
누군가 포트 8080에서 컴퓨터에 액세스하려고 하면 "Hello World!" 메시지가 표시됩니다.

<br/>
<br/>

:arrow_forward:[04 Modules](./04%20Modules.md) :arrow_forward:
