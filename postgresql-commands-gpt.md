
# 📋 PostgreSQL Common Commands Cheat Sheet

A categorized reference of frequently used PostgreSQL commands.

---

## 🏗️ Database Commands

| Command                                | Description                           |
|----------------------------------------|---------------------------------------|
| `CREATE DATABASE dbname;`              | Create a new database                 |
| `DROP DATABASE dbname;`                | Delete a database                     |
| `\l` or `\list`                        | List all databases                    |
| `\c dbname`                            | Connect to a specific database        |
| `\q`                                   | Quit the psql command-line tool       |

---

## 📦 Table Commands

| Command                                                  | Description                          |
|-----------------------------------------------------------|--------------------------------------|
| `CREATE TABLE tablename (...);`                          | Create a new table                   |
| `DROP TABLE tablename;`                                  | Delete a table                       |
| `TRUNCATE TABLE tablename;`                              | Delete all rows (fast)               |
| `ALTER TABLE tablename ADD COLUMN column_name TYPE;`     | Add a new column                     |
| `ALTER TABLE tablename DROP COLUMN column_name;`         | Remove a column                      |
| `ALTER TABLE tablename RENAME COLUMN a TO b;`            | Rename a column                      |
| `ALTER TABLE tablename RENAME TO newname;`               | Rename a table                       |
| `ALTER TABLE tablename ALTER COLUMN col TYPE newtype;`   | Change a column’s data type          |

---

## ✍️ Data Manipulation (DML)

| Command                                                                  | Description                    |
|---------------------------------------------------------------------------|--------------------------------|
| `INSERT INTO tablename (col1, col2) VALUES (val1, val2);`                | Insert a new row               |
| `SELECT * FROM tablename;`                                               | Retrieve all rows              |
| `SELECT name, age FROM tablename WHERE age > 18;`                        | Conditional SELECT             |
| `UPDATE tablename SET col = val WHERE condition;`                        | Update data                    |
| `DELETE FROM tablename WHERE condition;`                                 | Delete specific row(s)         |
| `DELETE FROM tablename;`                                                 | Delete all rows (⚠️ danger)    |

---

## 📌 Constraints

| Command                                                           | Description                          |
|--------------------------------------------------------------------|--------------------------------------|
| `PRIMARY KEY`, `UNIQUE`, `NOT NULL`, `CHECK`, `FOREIGN KEY`       | Column-level constraints             |
| `ALTER TABLE tablename ADD CONSTRAINT name UNIQUE (column);`      | Add a constraint                     |
| `ALTER TABLE tablename DROP CONSTRAINT name;`                     | Drop a constraint                    |

---

## ⚙️ Indexes

| Command                                        | Description                  |
|-----------------------------------------------|------------------------------|
| `CREATE INDEX idx_name ON tablename(column);` | Create an index             |
| `DROP INDEX idx_name;`                        | Drop an index               |

---

## 👥 User and Role Management

| Command                                                       | Description                       |
|----------------------------------------------------------------|-----------------------------------|
| `CREATE USER username WITH PASSWORD 'password';`              | Create a new user                |
| `CREATE ROLE role_name;`                                      | Create a new role                |
| `GRANT ALL PRIVILEGES ON DATABASE db TO username;`            | Grant privileges to a user       |
| `REVOKE ALL PRIVILEGES ON DATABASE db FROM username;`         | Revoke privileges from a user    |
| `\du`                                                         | List all roles                   |

---

## ⏱️ Transaction Control

| Command        | Description                          |
|----------------|--------------------------------------|
| `BEGIN;`       | Start a transaction                  |
| `COMMIT;`      | Save changes                         |
| `ROLLBACK;`    | Undo changes                         |

---

## 📄 Meta Commands (psql only)

| Command          | Description                     |
|------------------|---------------------------------|
| `\dt`            | List tables                     |
| `\d tablename`   | Describe a table structure       |
| `\dn`            | List schemas                    |
| `\df`            | List functions                  |
| `\dv`            | List views                      |
| `\dx`            | List extensions                 |

---

## 🧠 Advanced Features

### JSON & Arrays

| Command                                                       | Description                      |
|----------------------------------------------------------------|----------------------------------|
| `SELECT data->>'name' FROM tab;`                              | Get value from JSON              |
| `SELECT * FROM tab WHERE 'val' = ANY(array_col);`             | Check value in array             |

### COPY / Import / Export

| Command                                                       | Description                      |
|----------------------------------------------------------------|----------------------------------|
| `COPY tablename FROM '/path/to/file.csv' CSV HEADER;`         | Import CSV file                  |
| `COPY tablename TO '/path/to/file.csv' CSV HEADER;`           | Export table to CSV              |

### Extensions

| Command                                    | Description                |
|--------------------------------------------|----------------------------|
| `CREATE EXTENSION IF NOT EXISTS "uuid-ossp";` | Enable UUID generation     |
| `CREATE EXTENSION IF NOT EXISTS "pgcrypto";`  | Enable crypto functions     |

---

## 🧪 Utility

| Command                         | Description                      |
|----------------------------------|----------------------------------|
| `EXPLAIN SELECT ...;`           | Show query execution plan        |
| `ANALYZE tablename;`            | Update table statistics          |
| `VACUUM;`                       | Clean up dead tuples             |
