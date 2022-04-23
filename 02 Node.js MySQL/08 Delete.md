# 08 Delete

## 1. Delete Record

`DELETE FROM` 문을 사용하여 기존 테이블에서 레코드를 삭제할 수 있습니다.

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
  var sql = "DELETE FROM customers WHERE address = 'Mountain 21'";
  con.query(sql, function (err, result) {
    if (err) throw err;
    console.log("Number of records deleted: " + result.affectedRows);
  });
});
```

<br />
<br />

## 2. The Result Object

결과를 실행하면 결과 개체가 반환됩니다.

```javascript
console.log(result.affectedRows);
```

<br />
<br />

:arrow_forward:[09 Drop Table](./09%20Drop%20Table.md):arrow_forward:
