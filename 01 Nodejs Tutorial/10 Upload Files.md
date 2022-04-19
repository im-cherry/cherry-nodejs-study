# 10 Upload Files

## 1. The Formidable Module - 강력한 모듈

`Formidable` 은 파일 업로드 작업을 위한 아주 좋은 모듈입니다.

```
$ npm install formidable
```

```
var formidable = require("formidable")
```

<br />
<br />

## 2. Upload Files

Node.js에서 사용자가 컴퓨터에 파일을 업로드할 수 있는 웹 페이지를 만듭니다.

<br/>

### 1) Create an Upload Form

업로드 필드가 있는 HTML 양식을 작성하는 Node.js 파일을 만듭니다.

```javascript
var http = require("http");

http
  .createServer(function (req, res) {
    res.writeHead(200, { "Content-Type": "text/html" });
    res.write(
      "<form action=`fileupload` method=`post` enctype=`multipart/form-data`>"
    );
    res.write("<input type=`file` name=`fileupload` /><br />");
    res.write("<input type=`submit` />");
    res.write("</form>");
    return res.end();
  })
  .listen(8080);
```

<br/>

### 2) Parse the Uploaded File

업로드된 파일이 서버에 도달하면 이를 구문 분석할 수 있도록 Formidable 모듈을 포함합니다.  
파일이 업로드되고 구문 분석되면 컴퓨터의 임시 폴더에 저장됩니다.

```javascript
var http = require("http");
var formidable = require("formidable");

http
  .createServer(function (req, res) {
    if (req.url == "/fileupload") {
      var from = new formidable.IncomingForm();
      form.parse(req, function (err, fields, files) {
        res.write("File uploaded");
        res.end();
      });
    } else {
      res.writeHead(200, { "Content-Type": "text/html" });
      res.write(
        "<form action=`fileupload` method=`post` enctype=`multipart/form-data`>"
      );
      res.write("<input type=`file` name=`fileupload` /><br />");
      res.write("<input type=`submit` />");
      res.write("</form>");
      return res.end();
    }
  })
  .listen("8080");
```

<br/>

### 3) Save the File

파일 서버에 성공적으로 업로드되면 임시 폴더에 저장됩니다.  
이 디렉토리의 경로는 `parse()` 메서드의 콜백 함수에서 3번째 인수로 전달된 `files` 개체에서 찾을 수 있습니다.  
파일을 선택한 폴더로 이동하려면 `fs` 모듈을 사용하여 파일 이름을 변경합니다.

```javascript
var http = require("http");
var formidable = require("formidable");
var fs = require("fs");

http
  .createServer(function (req, res) {
    if (req.url == "/fileupload") {
      var form = new formidable.IncomingForm();
      form.parse(rqe, function (err, fields, files) {
        var oldpath = files.filetoupload.filepath;
        var newpath =
          "C:/Users/Your Name/" + files.filetoupload.originalFilename;
        fs.rename(oldpath, newpath, function (err) {
          if (err) throw err;
          res.write("File uploaded and moved!");
          res.end;
        });
      });
    } else {
      res.writeHead(200, { "Content-Type": "text/html" });
      res.write(
        "<form action=`fileupload` method=`post` enctype=`multipart/form-data`>"
      );
      res.write("<input type=`file` name=`fileupload` /><br />");
      res.write("<input type=`submit` />");
      res.write("</form>");
      return res.end();
    }
  })
  .listen(8080);
```

<br />
<br />

:arrow_forward:[11 Email](./11%20Email.md) :arrow_forward:
