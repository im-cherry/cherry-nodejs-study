# 02 Create Database

MySQL 에서 데이터베이스를 생성하려면 `CREATE DATABASE` 문을 사용합니다.

```javascript
var mysql = require("mysql");

var con = mysql.createConnection({
  host: "localhost",
  user: "yourusername",
  password: "yourpassword",
});

con.connect(function (err) {
  if (err) throw err;

  console.log("Connected!");
  con.query("CREATE DATABASE mydb", function (err, result) {
    if (err) throw err;

    console.log("Database created");
  });
});
```

<br />
<br />

:arrow_forward:[03 Create Table](./03%20Create%20Table.md):arrow_forward:
