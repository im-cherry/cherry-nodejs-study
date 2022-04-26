# 02 express

## 1. express 설치와 사용

```
$ npm install express
$ npm install -D nodemon
```

<br/>
<br/>

## 2. express 사용법

```javascript
const express = require("express");
const app = express();

app.get("/", (req, res) => {
  res.send("Hello World!");
});

app.listen(8080, () => {
  console.log("8080 포트에서 서버 실행 중...");
});
```

```javascript
const express = require("express");
const app = express();
app.set("port", process.env.PORT || 8080);

app.get("/", (req, res) => {
  res.sendFile(__dirname + "/index.html");
});

app.listen(app.get("port"), () => {
  console.log(app.get("port"), " 포트에서 서버 실행 중...");
});
```

<br/>
<br/>

:arrow_forward:[03 middleware](./03%20middleware.md):arrow_forward:
