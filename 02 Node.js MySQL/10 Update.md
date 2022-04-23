# 10 Update

## 1. Update Table

`UPDATE` 문을 사용하여 테이블의 기존 레코드를 업데이트할 수 있습니다.

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
  var sql =
    "UPDATE customers SET address = 'Canyon 123' WHERE address = 'Valley 345'";
  con.query(sql, function (err, result) {
    if (err) throw err;
    console.log(result.affectedRows + " record(s) updated");
  });
});
```

<br />
<br />

## 2. The Result Object

결과 개체에는 쿼리가 테이블에 어떤 영향을 미쳤는지에 댛나 정보가 포함되어 있습니다.

```javascript
console.log(result.affectedRows);
```

<br />
<br />

:arrow_forward:[11 Limit](./11%20Limit.md):arrow_forward:
