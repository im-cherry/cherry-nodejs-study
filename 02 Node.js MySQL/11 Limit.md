# 11 Limit

## 1. Limit the Result

`LIMIT` 문을 사용하여 쿼리에서 반환되는 레코드 수를 제한할 수 있습니다.

```javascript
var mysql = require("mysql");

var con = mysql.createConnection({
  host: "localhost",
  user: "yourusername",
  password: "yourpassword",
  database: "mydb",
});

con.connect(function (err) {
  if (err) throw err;
  var sql = "SELECT * FROM customers LIMIT 5";
  con.query(sql, function (err, result) {
    if (err) throw err;
    console.log(result);
  });
});
```

<br />
<br />

## 2. Start From Another Position

`OFFSET` 키워드를 사용하면 쿼리에서 반환되는 레코드의 시작 위치를 설정할 수 있습니다..

```javascript
var mysql = require("mysql");

var con = mysql.createConnection({
  host: "localhost",
  user: "yourusername",
  password: "yourpassword",
  database: "mydb",
});

con.connect(function (err) {
  if (err) throw err;
  var sql = "SELECT * FROM customers LIMIT 5 OFFSET 2";
  con.query(sql, function (err, result) {
    if (err) throw err;
    console.log(result);
  });
});
```

<br />
<br />

## 3. Shorter Syntax

```javascript
var mysql = require("mysql");

var con = mysql.createConnection({
  host: "localhost",
  user: "yourusername",
  password: "yourpassword",
  database: "mydb",
});

con.connect(function (err) {
  if (err) throw err;
  var sql = "SELECT * FROM customers LIMIT 2, 5"; // 위치 3에서 시작하여 5개 레코드 반환
  con.query(sql, function (err, result) {
    if (err) throw err;
    console.log(result);
  });
});
```

<br />
<br />

:arrow_forward:[12 Join](./12%20Join.md):arrow_forward:
