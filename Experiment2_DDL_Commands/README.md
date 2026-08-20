# Experiment 2: DDL Commands

## AIM
To study and implement DDL commands and different types of constraints.

## THEORY

### 1. CREATE
Used to create a new relation (table).

**Syntax:**
```sql
CREATE TABLE (
  field_1 data_type(size),
  field_2 data_type(size),
  ...
);
```
### 2. ALTER
Used to add, modify, drop, or rename fields in an existing relation.
(a) ADD
```sql
ALTER TABLE std ADD (Address CHAR(10));
```
(b) MODIFY
```sql
ALTER TABLE relation_name MODIFY (field_1 new_data_type(size));
```
(c) DROP
```sql
ALTER TABLE relation_name DROP COLUMN field_name;
```
(d) RENAME
```sql
ALTER TABLE relation_name RENAME COLUMN old_field_name TO new_field_name;
```
### 3. DROP TABLE
Used to permanently delete the structure and data of a table.
```sql
DROP TABLE relation_name;
```
### 4. RENAME
Used to rename an existing database object.
```sql
RENAME TABLE old_relation_name TO new_relation_name;
```
### CONSTRAINTS
Constraints are used to specify rules for the data in a table. If there is any violation between the constraint and the data action, the action is aborted by the constraint. It can be specified when the table is created (using CREATE TABLE) or after it is created (using ALTER TABLE).
### 1. NOT NULL
When a column is defined as NOT NULL, it becomes mandatory to enter a value in that column.
Syntax:
```sql
CREATE TABLE Table_Name (
  column_name data_type(size) NOT NULL
);
```
### 2. UNIQUE
Ensures that values in a column are unique.
Syntax:
```sql
CREATE TABLE Table_Name (
  column_name data_type(size) UNIQUE
);
```
### 3. CHECK
Specifies a condition that each row must satisfy.
Syntax:
```sql
CREATE TABLE Table_Name (
  column_name data_type(size) CHECK (logical_expression)
);
```
### 4. PRIMARY KEY
Used to uniquely identify each record in a table.
Properties:
Must contain unique values.
Cannot be null.
Should contain minimal fields.
Syntax:
```sql
CREATE TABLE Table_Name (
  column_name data_type(size) PRIMARY KEY
);
```
### 5. FOREIGN KEY
Used to reference the primary key of another table.
Syntax:
```sql
CREATE TABLE Table_Name (
  column_name data_type(size),
  FOREIGN KEY (column_name) REFERENCES other_table(column)
);
```
### 6. DEFAULT
Used to insert a default value into a column if no value is specified.

Syntax:
```sql
CREATE TABLE Table_Name (
  col_name1 data_type,
  col_name2 data_type,
  col_name3 data_type DEFAULT 'default_value'
);
```

**Question 1**
--
<img width="1242" height="402" alt="exp1" src="https://github.com/user-attachments/assets/ffb19b20-fffa-4d6f-91b2-4942d1a9f077" />


```sql
CREATE TABLE Bonuses (
    BonusID INTEGER PRIMARY KEY,
    EmployeeID INTEGER,
    BonusAmount REAL CHECK (BonusAmount > 0),
    BonusDate DATE,
    Reason TEXT NOT NULL,
    FOREIGN KEY (EmployeeID) REFERENCES Employees(EmployeeID)
);
```

**Output:**

<img width="1241" height="374" alt="exp1 1" src="https://github.com/user-attachments/assets/99bd3696-a33c-41ea-9def-5590297f4faa" />

**Question 2**
---
<img width="1232" height="514" alt="exp1 2" src="https://github.com/user-attachments/assets/2d977ba4-6660-4f09-96fe-7682e1eb0156" />

```sql
ALTER TABLE Companies RENAME COLUMN name TO first_name;

ALTER TABLE Companies ADD COLUMN mobilenumber number;

ALTER TABLE Companies ADD COLUMN DOB Date;
```

**Output:**

<img width="1243" height="480" alt="exp1 3" src="https://github.com/user-attachments/assets/257cd8dd-c1aa-423d-921f-b3d4a400c833" />

**Question 3**
---
<img width="1269" height="493" alt="exp1 4" src="https://github.com/user-attachments/assets/ef362d6c-035e-41dc-803c-8c7c5d4d68e8" />

```sql
INSERT INTO Books (ISBN, Title, Author, Publisher, Year)
VALUES ('978-1234567890', 'Introduction to AI', 'John Doe', NULL, NULL);

INSERT INTO Books (ISBN, Title, Author, Publisher, Year)
VALUES ('978-9876543210', 'Deep Learning', 'Jane Doe', 'TechPress', 2022);

INSERT INTO Books (ISBN, Title, Author, Publisher, Year)
VALUES ('978-1122334455', 'Cybersecurity Essentials', 'Alice Smith', NULL, 2021);
```

**Output:**

<img width="1232" height="371" alt="exp1 5" src="https://github.com/user-attachments/assets/508a19a8-81f1-4cd4-b2ec-48d54c569f58" />

**Question 4**
---
<img width="1220" height="311" alt="exp1 6" src="https://github.com/user-attachments/assets/26551e78-8f2d-4efe-bfb4-8f2bd3e50669" />

```sql
CREATE TABLE jobs (
    job_id INTEGER,
    job_title TEXT DEFAULT '',
    min_salary INTEGER DEFAULT 8000,
    max_salary INTEGER DEFAULT NULL
);
```

**Output:**

<img width="1227" height="402" alt="exp1 7" src="https://github.com/user-attachments/assets/cd1a6197-5436-4dff-bf14-ece37c061ac8" />

**Question 5**
---
<img width="1123" height="417" alt="exp1 8" src="https://github.com/user-attachments/assets/03fff541-8b79-4658-bb19-ba5456e73954" />

```sql
CREATE TABLE Orders (
    OrderID INTEGER,
    OrderDate TEXT,
    CustomerID INTEGER
);
```

**Output:**

<img width="1235" height="471" alt="exp1 9" src="https://github.com/user-attachments/assets/54111857-cc5c-4af4-9da2-19ce5c4038b5" />

**Question 6**
---

<img width="1090" height="476" alt="exp1 10" src="https://github.com/user-attachments/assets/d80ad7b8-2419-4856-af55-3b249c30a7bc" />


```sql
CREATE TABLE item (
    item_id TEXT PRIMARY KEY,
    item_desc TEXT NOT NULL,
    rate INTEGER NOT NULL,
    icom_id TEXT,
    FOREIGN KEY (icom_id)
        REFERENCES company(com_id)
        ON UPDATE CASCADE
        ON DELETE CASCADE
);
```

**Output:**

<img width="1242" height="434" alt="exp1 11" src="https://github.com/user-attachments/assets/60ec4ffc-207a-4f1e-8c07-3aaf6e9f601c" />


**Question 7**
---
<img width="1079" height="369" alt="exp1 12" src="https://github.com/user-attachments/assets/f2a44a57-5c56-4f8a-9719-e6d177aa65da" />

```sql
INSERT INTO Customers (CustomerID, Name, Address, Email)
SELECT CustomerID, Name, Address, Email
FROM Old_customers;
```

**Output:**

<img width="1231" height="381" alt="exp 1 13" src="https://github.com/user-attachments/assets/13278387-2f97-4abf-8776-3c5280a6877e" />

**Question 8**
---
<img width="1228" height="509" alt="exp1 13" src="https://github.com/user-attachments/assets/1fb6178c-9df6-4b74-9964-a1087ce6d335" />

```sql
INSERT INTO Customers (CustomerID, Name, Address, City, ZipCode)
VALUES (306, 'Diana Prince', 'Themyscira', NULL, NULL);

INSERT INTO Customers (CustomerID, Name, Address, City, ZipCode)
VALUES (307, 'Bruce Wayne', 'Wayne Manor', 'Gotham', 10007);

INSERT INTO Customers (CustomerID, Name, Address, City, ZipCode)
VALUES (308, 'Peter Parker', 'Queens', NULL, 11375);
```

**Output:**

<img width="1238" height="378" alt="exp1 14" src="https://github.com/user-attachments/assets/f9c5129b-ec1c-44b1-98a6-46e015338cac" />

**Question 9**
---
<img width="1199" height="469" alt="exp1 15" src="https://github.com/user-attachments/assets/a75535a0-fd6c-4612-bac7-1eb81b35e74f" />

```sql
ALTER TABLE Companies RENAME COLUMN name TO first_name;

ALTER TABLE Companies ADD COLUMN mobilenumber number;

ALTER TABLE Companies ADD COLUMN DOB Date;

ALTER TABLE Companies ADD COLUMN State varchar(30);
```

**Output:**
<img width="1236" height="494" alt="exp1 16" src="https://github.com/user-attachments/assets/d819bf61-0a8f-4b8c-9007-e2d8e7aff6d5" />


**Question 10**
---

<img width="1102" height="358" alt="exp1 17" src="https://github.com/user-attachments/assets/dbf33582-24a0-45f8-99ed-3a986ca0fa93" />

```sql
CREATE TABLE Invoices (
    InvoiceID INTEGER PRIMARY KEY,
    InvoiceDate DATE,
    DueDate DATE CHECK (DueDate > InvoiceDate),
    Amount REAL CHECK (Amount > 0)
);
```

**Output:**

<img width="1232" height="357" alt="exp1 18" src="https://github.com/user-attachments/assets/7a191876-9128-4d74-b911-728dfe01180f" />


## RESULT
Thus, the SQL queries to implement different types of constraints and DDL commands have been executed successfully.
