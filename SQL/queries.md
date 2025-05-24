## Login to PostgreSQL using :
psql -U postgres
## To list databases:
\l
## Create new database
CREATE DATABASE testdb;
## To connect to a database (e.g., testdb):
\c testdb
(testdb is database name)
## Check available tables:
\dt
## Display Table Data:
SELECT * FROM class;
(class is table name)
##  Create new table and insert data:
```js
CREATE TABLE students (
  id SERIAL PRIMARY KEY,
  name VARCHAR(100),
  age INT
);

INSERT INTO students (name, age) VALUES ('Alice', 20), ('Bob', 22);
```