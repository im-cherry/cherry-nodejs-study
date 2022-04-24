# 05 Nodejs 내장 모듈과 객체

## 1. Path

path 모듈은 파일과 디렉토리 경로 작업을 위한 유틸리티를 제공합니다.

```javascript
const path = require("path");

console.log(__filename); // 현재 파일의 절대 경로
console.log(path.basename(__filename)); // 경로의 마지막 부분
console.log(path.basename(__filename, ".js")); // 경로의 자미작 부분에서 확장자를 제거한 이름
console.log(path.dirname(__filename)); // 파일이 위치한 디렉토리(폴더 경로)
console.log(path.extname("index.html")); // 파일의 확장자
path.format({
  root: "/",
  dir: "/home/user/dir",
  base: "file.txt",
  // name: "file",
  // ext: ".txt"
}); // pathObject를 문자열로 반환
path.parse("/home/user/dir/file.txt"); // 문자열로된 경로를 pathObject로 반환
```

<br/>
<br/>

## 2. URL

url 모듈은 인터넷 주소에 해당하는 url 을 다루기 위한 모듈입니다.

```javascript
const url = require("url");

const myURL = new URL(
  "https://user:pass@sub.example.com:8080/p/a/t/h?query=string#hash"
);
console.log(url.parse(myURL));
```

```javascript
const url = require("url");

const myURL = new URL("https://example.org/?user=abc&query=xyz");
console.log(myURL.searchParams.get("user"));
console.log(myURL.searchParams.has("user"));
console.log(myURL.searchParams.keys());
console.log(myURL.searchParams.values());
```

<br/>
<br/>

## 3. Crypto

crypto 모듈은 다양한 암호화 기능을 제공합니다.

```javascript
const crypto = require("crypto");

crypto.createHash("sha512").update("pw1234").digest("base64");
crypto.createHash("sha512").update("pw1234").digest("hex");
```

<br/>
<br/>

## 4. File system

fs 모듈은 파일 읽기, 쓰기, 삭제 그리고 폴더 생성, 삭제 등과 같은 파일 처리와 관련되 작업을 위한 모듈입니다.

```javascript
const fs = require("fs");

// 파일 읽기
fs.readFile("./sample/text.txt", "utf8", (err, data) => {
  if (err) {
    throw err;
  }

  console.log(data);
});

// 파일 쓰기
let data = "파일 읽기 테스트";
fs.writeFile("./sample/text_w.txt", data, "utf8", (err) => {
  if (err) {
    throw err;
  }

  console.log("파일 쓰기 완료");
});

// sql 파일이 변경 되면(쿼리문이 수정되거나 추가되면), 이를 감지하고 반영
let sql = require("./sql.js");

fs.watchFile(__dirname + "/sql.js", (curr, prev) => {
  console.log("sql 변경 시 재시작 없이 반영되도록 함");
  delete require.cache[require.resolve("./sql.js")]; // 캐시에 저장되어 있는 파일 삭제
  sql = require("./sql.js"); // sql.js 파일에 변경이 일어날 때마다 sql.js 재할당
});
```

<br/>
<br/>

:arrow_forward:[06 json-server 이용하기](./06%20json-server%20%EC%9D%B4%EC%9A%A9%ED%95%98%EA%B8%B0.md):arrow_forward:
