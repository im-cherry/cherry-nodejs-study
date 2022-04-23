# 06 File System

## 1. Node.js as a File Server

- Node.js 파일 시스템 모듈을 사용하면 컴퓨터의 파일 시스템으로 작업할 수 있습니다.

  ```javascript
  var fs = require("fs");
  ```

- 파일 시스템 모듈의 일반적인 용도
  - 파일 read
  - 파일 crete
  - 파일 update
  - 파일 delete
  - 파일 이름 rename

<br/>
<br/>

## 2. Read Files

`fs.readFile()` 은 컴퓨터에서 파일을 읽는 데 사용됩니다.

```html
<html>
  <body>
    <h1>My Header</h1>
    <p>My paragraph.</p>
  </body>
</html>
```

```javascript
var http = require("http");
var fs = require("fs");
http
  .createServer(function (req, res) {
    fs.readFile("index.html", function (err, data) {
      res.writeHead(200, { "Content-Type": "text/html" });
      res.write(data);
      return res.end();
    });
  })
  .listen(8080);
```

<br/>
<br/>

## 3. Create Files

파일 시스템 모듈에는 새 파일을 만드는 방법이 있습니다.

- fs.appendFile()

  ```javascript
  var fs = require("fs");

  fs.appendFile("myfile1.txt", "Hello content!", function (err) {
    if (err) throw err;
    console.log("Saved!");
  });
  ```

- fs.open()

  ```javascript
  var fs = require("fs");

  fs.open("myfile2.txt", "w", function (err, file) {
    if (err) throw err;
    console.log("Saved!");
  });
  ```

- fs.writeFile()

  ```javascript
  var fs = require("fs");

  fs.writeFile("myfile3.txt", "Hello content!", function (err) {
    if (err) throw err;
    console.log("Saved!");
  });
  ```

<br/>
<br/>

## 4. Update Files

파일 시스템 모듈에는 파일 업데이트 방법이 있습니다.

- fs.appendFile() : 파일의 끝에 내용을 추가

  ```javascript
  var fs = require("fs");

  fs.appendFile("myfile1.txt", "This is my text", function (err) {
    if (err) throw err;
    console.log("Updated!");
  });
  ```

- fs.writeFile() : 파일 내용 변경

```javascript
fs.writeFile("myfile3.txt", "This is my text", function (err) {
  if (err) throw err;
  console.log("Replaced!");
});
```

<br/>
<br/>

## 5. Delete Files

파일 시스템 모듈로 파일을 삭제하려면 `fs.unlink()` 메서드를 사용합니다.

```javascript
var fs = require("fs");

fs.unlink("myfile2.txt", function (err) {
  if (err) throw err;
  console.log("File deleted!");
});
```

<br/>
<br/>

## 6. Rename Files

파일 시스템 모듈을 사용하여 파일의 이름을 바꾸려면 `fs.rename()` 메서드를 사용합니다.

```javascript
var fs = require("fs");

fs.rename("myfile1.txt", "myrenamedfile.txt", function (err) {
  if (err) throw err;
  console.log("File Renamed!");
});
```

<br/>
<br/>

:arrow_forward:[07 URL Module](./07%20URL%20Module.md) :arrow_forward:
