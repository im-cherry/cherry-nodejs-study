# 03 Create Table

## 1. Creating a Table

MySQL 에서 테이블을 생성하려면 `CREATE TABLE` 문을 사용합니다.

- demo_create_table.js

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
    console.log("Connected!");
    var sql =
      "CREATE TABLE customers (name VARCHAR(255), address VARCHAR(255))";
    con.query(sql, function (err, result) {
      if (err) throw err;
      console.log("Table created!");
    });
  });
  ```

```
$ node demo_create_table.js
```

<br />
<br />

## 2. Primary Key

테이블을 생성할 때 각 레코드에 대해 고유한 키가 있는 열도 생성해야 합니다.  
각 레코드에 대해 고유 번호는 삽입할 `INT AUTO_INCREMENT PRIMARY KEY`로 열을 정의하여 수행할 수 있습니다.  
1에서 시작하여 각 레코드에 대해 1씩 증가합니다.

```javascript
var mysql = require("mysql");

var con = mysql.createConnection({
  host: "localhost",
  user: "yourusername",
  password: "youpassword",
  database: "mydb",
});

con.connect(function (err) {
  if (err) throw err;
  console.log("Connected!");
  var sql =
    "CREATE TABLE customers (id INT AUTO_INCREMENT PRIMARY KEY, name VARCHAR(255), address VARCHAR(255))";
  con.query(sql, function (err, result) {
    if (err) throw err;
    console.log("Table created");
  });
});
```

테이블이 이미 있는 경우 `ALTER TABLE` 키워드를 사용합니다.

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
  console.log("Connected!");
  var sql =
    "ALTER TABLE customers ADD COLUMN id INT AUTO_INCREMENT PRIMARY KEY";
  con.query(sql, function (err, result) {
    if (err) throw err;
    console.log("Table altered");
  });
});
```

<br />
<br />

:arrow_forward:[04 Insert Into](./04%20Insert%20Into.md):arrow_forward:
