# 04 Insert Into

## 1. Insert Into Table

MySQL에서 테이블을 채우려면 `INSERT INTO`문을 사용합니다.

- demo_db_insert.js

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
    "INSERT INTO customers (name, address) VALUES ('Company Inc', 'Highwqy 37')";
  con.query(sql, function (err, result) {
    if (err) throw err;
    console.log("1 record inserted");
  });
});
```

```
$ node demo_db_insert.js
```

<br />
<br />

## 2. Insert Multiple Records

둘 이상의 레코드를 삽입하려면 값을 포함하는 배열을 만들고, 값 배열로 대체될 sql에 `?`을 삽입합니다.

- demo_db_insert_multiple.js

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
    var sql = "INSERT INTO customers (name, address) VALUES ?";
    var values = [
      ["John", "Highway 71"],
      ["Peter", "Lowstreet 4"],
      ["Amy", "Apple st 652"],
      ["Hannah", "Mountain 21"],
      ["Michael", "Valley 345"],
      ["Sandy", "Ocean blvd 2"],
      ["Betty", "Green Grass 1"],
      ["Richard", "Sky st 331"],
      ["Susan", "One way 98"],
      ["Vicky", "Yellow Garden 2"],
      ["Ben", "Park Lane 38"],
      ["William", "Central st 954"],
      ["Chuck", "Main Road 989"],
      ["Viola", "Sideway 1633"],
    ];
    con.query(sql, [values], function (err, result) {
      if (err) throw err;
      console.log("Number of records inserted: " + result.affectedRows);
    });
  });
  ```

```
$ node demo_db_insert_multiple.js
```

<br />
<br />

## 3. The Result Object

쿼리를 실행하면 결과 객체가 반환됩니다.  
결과 객체에는 쿼리가 테이블에 어떤 영향을 미쳤는지에 대한 정보가 포함되어 있습니다.

```
{
  fieldCount: 0,
  affectedRows: 14,
  insertId: 0,
  serverStatus: 2,
  warningCount: 0,
  message: '\'Records:14  Duplicated: 0  Warnings: 0',
  protocol41: true,
  changedRows: 0
}
```

<br />
<br />

## 4. Get Inserted ID

자동 증가 ID 필드가 있는 테이블의 경우 결과 개체를 요청하여 방금 삽입한 행의 ID를 얻을 수 있습니다.

- demo_db_insert_id.js

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
    "INSERT INTO customers (name, address) VALUES ('Michelle', 'Blue Village 1')";
  con.query(sql, function (err, result) {
    if (err) throw err;
    console.log("1 record inserted, ID: " + result.insertId);
  });
});
```

```
$ node demo_db_insert_id.js
```

<br />
<br />

:arrow_forward:[05 Select From](./05%20Select%20From.md):arrow_forward:
