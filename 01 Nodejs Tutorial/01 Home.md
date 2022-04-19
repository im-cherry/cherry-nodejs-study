# 01 Home

Nodejs는 오픈 소스 서버 환경입니다.  
Nodejs를 사용하면 서버에서 JavaScript를 실행할 수 있습니다.

<br/>

## 1. Learning by Examples

```javascript
var http = require("http");

http
  .createServer(function (req, res) {
    res.writeHead(200, { "Content-Type": "text/plain" });
    res.end("Hello World!");
  })
  .listen(8000);
```

<br/>
<br/>

## 2. Examples Running in the Command Line Interface

```
$ node demo_intro_cmd.js
This example is different!
The result is displayed in the Command Line Interface
```

- demo_intro_cmd.js

  ```javascript
  console.log("This example is different!");
  console.log("The result is displayed in the Command Line Interface");
  ```

<br/>
<br/>

## 3. Download Node.js

[Node.js 공식 웹사이트](https://nodejs.org/en/)에서 Node.js를 다운로드 하세요.

<br/>
<br/>

[02 Intro](./02%20Intro.md)
