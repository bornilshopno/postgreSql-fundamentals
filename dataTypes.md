# PostgreSQL Data Types with Examples

This document provides a categorized list of PostgreSQL data types along with usage examples.

---

## 🔢 NUMERIC TYPES

| Data Type         | Description                                      | Example Usage                      |
|------------------|--------------------------------------------------|------------------------------------|
| SMALLINT          | 2-byte integer                                   | `age SMALLINT`                     |
| INTEGER / INT     | 4-byte integer                                   | `quantity INTEGER`                 |
| BIGINT            | 8-byte integer                                   | `views BIGINT`                     |
| DECIMAL(p, s)     | Exact number with precision and scale            | `price DECIMAL(10, 2)`             |
| NUMERIC(p, s)     | Same as DECIMAL                                  | `tax NUMERIC(5, 2)`                |
| REAL              | 4-byte floating-point (approximate)              | `rating REAL`                      |
| DOUBLE PRECISION  | 8-byte floating-point (approximate)              | `temperature DOUBLE PRECISION`     |
| SERIAL            | Auto-incrementing 4-byte integer                 | `id SERIAL PRIMARY KEY`            |
| BIGSERIAL         | Auto-incrementing 8-byte integer                 | `order_id BIGSERIAL`               |

---

## 🔤 CHARACTER TYPES

| Data Type  | Description                      | Example Usage                          |
|------------|----------------------------------|----------------------------------------|
| CHAR(n)    | Fixed-length string              | `code CHAR(5)`                         |
| VARCHAR(n) | Variable-length string           | `username VARCHAR(50)`                 |
| TEXT       | Variable unlimited-length string | `bio TEXT`                             |

---

## 📅 DATE AND TIME TYPES

| Data Type               | Description                         | Example Usage                              |
|-------------------------|-------------------------------------|--------------------------------------------|
| DATE                    | Calendar date                       | `dob DATE`                                 |
| TIME                    | Time without time zone              | `start_time TIME`                          |
| TIME WITH TIME ZONE     | Time with time zone                 | `departure_time TIME WITH TIME ZONE`       |
| TIMESTAMP               | Date and time without time zone     | `created_at TIMESTAMP`                     |
| TIMESTAMPTZ             | Date and time with time zone        | `updated_at TIMESTAMPTZ`                   |
| INTERVAL                | Time duration                       | `duration INTERVAL`                        |

---

## ✅ BOOLEAN TYPE

| Data Type | Description                    | Example Usage             |
|-----------|--------------------------------|---------------------------|
| BOOLEAN   | Stores TRUE, FALSE, or NULL    | `is_active BOOLEAN`       |

---

## 🧾 TEXT SEARCH / DOCUMENT TYPES

| Data Type | Description                   | Example Usage             |
|-----------|-------------------------------|---------------------------|
| TSVECTOR  | Document for full-text search | `content TSVECTOR`        |
| TSQUERY   | Query for full-text search    | `SELECT * WHERE text @@ query` |

---

## 🧩 ARRAY TYPES

| Data Type    | Description                       | Example Usage                 |
|--------------|-----------------------------------|-------------------------------|
| ANYTYPE[]    | Array of any base type            | `tags TEXT[]`                 |

---

## 📦 BINARY DATA TYPES

| Data Type | Description            | Example Usage            |
|-----------|------------------------|--------------------------|
| BYTEA     | Binary data            | `file_data BYTEA`        |

---

## 🔘 UUID TYPE

| Data Type | Description                        | Example Usage                               |
|-----------|------------------------------------|---------------------------------------------|
| UUID      | Universally unique identifier      | `id UUID DEFAULT gen_random_uuid()`         |

> 🔧 Enable UUID generation:
> ```sql
> CREATE EXTENSION IF NOT EXISTS "pgcrypto";
> ```

---

## 🧠 JSON AND XML TYPES

| Data Type | Description            | Example Usage                      |
|-----------|------------------------|------------------------------------|
| JSON      | Text-based JSON data   | `profile JSON`                     |
| JSONB     | Binary JSON (indexed)  | `settings JSONB`                   |
| XML       | XML data               | `data XML`                         |

---

## 🗃️ ENUMERATED TYPE

| Data Type | Description                       | Example Usage                                     |
|-----------|-----------------------------------|--------------------------------------------------|
| ENUM      | Custom fixed list of values       | `status mood`<br>`CREATE TYPE mood AS ENUM (...)`|

---

## 📏 RANGE TYPES

| Data Type     | Description                  | Example Usage                     |
|---------------|------------------------------|-----------------------------------|
| int4range     | Range of INTEGER             | `active_years int4range`         |
| numrange      | Range of NUMERIC             | `salary_range numrange`          |
| tsrange       | Range of TIMESTAMP           | `booking_period tsrange`         |
| tstzrange     | Range of TIMESTAMPTZ         | `validity tstzrange`             |
| daterange     | Range of DATE                | `semester daterange`             |

---

## 🌐 NETWORK TYPES

| Data Type | Description           | Example Usage             |
|-----------|-----------------------|---------------------------|
| INET      | IP address            | `client_ip INET`          |
| CIDR      | Network address       | `network CIDR`            |
| MACADDR   | MAC address           | `device_mac MACADDR`      |

---

## 🔧 GEOMETRIC TYPES

| Data Type | Description           | Example Usage             |
|-----------|-----------------------|---------------------------|
| POINT     | (x, y) coordinate     | `location POINT`          |
| LINE      | Infinite line         | `road LINE`               |
| LSEG      | Line segment          | `segment LSEG`            |
| BOX       | Rectangular box       | `window BOX`              |
| CIRCLE    | Circle with radius    | `zone CIRCLE`             |
| POLYGON   | Shape with vertices   | `area POLYGON`            |

---

## 📌 Example Table Definition

```sql
CREATE TABLE products (
    product_id BIGSERIAL PRIMARY KEY,
    name TEXT NOT NULL,
    price NUMERIC(10, 2) NOT NULL,
    description TEXT,
    available BOOLEAN DEFAULT TRUE,
    tags TEXT[],
    created_at TIMESTAMPTZ DEFAULT CURRENT_TIMESTAMP
);
