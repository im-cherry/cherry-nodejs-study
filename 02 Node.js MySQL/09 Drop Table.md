# 09 Drop Table

## 1. Delete a Table

`DROP TABLE` 문을 사용하여 기존 테이블을 삭제할 수 있습니다.

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
  var sql = "DROP TABLE customers";
  con.query(sql, function (err, result) {
    if (err) throw err;
    console.log("Table deleted");
  });
});
```

<br />
<br />

## 2. Drop Only if Exist

삭제하려는 테이블이 이미 삭제되었거나 다른 이유로 존재하지 않는 경우 `IF EXISTS` 키워드를 사용하여 오류가 발생하지 않도록 할 수 있습니다.

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
  var sql = "DROP TABLE IF EXISTS customers";
  con.query(sql, function (err, result) {
    if (err) throw err;
    console.log(result);
  });
});
```

<br />
<br />

:arrow_forward:[10 Update](./10%20Update.md):arrow_forward:
