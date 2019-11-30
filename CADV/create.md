# Create 语法

<!-- TOC -->

- [Create 语法](#create-语法)
    - [语法](#语法)
        - [1. CREATE DATABASE 实例](#1-create-database-实例)
        - [2. CREATE TABLE 实例](#2-create-table-实例)
        - [3. NOT NULL 约束](#3-not-null-约束)
        - [4. UNIQUE 约束](#4-unique-约束)
        - [5. PRIMARY KEY 约束](#5-primary-key-约束)
        - [6. FOREIGN KEY 约束](#6-foreign-key-约束)
        - [7.  CHECK 约束](#7--check-约束)
        - [8. DEFAULT 约束](#8-default-约束)
        - [9. CREATE INDEX 语句](#9-create-index-语句)
        - [10. AUTO INCREMENT 字段](#10-auto-increment-字段)

<!-- /TOC -->

## 语法

### 1. CREATE DATABASE 实例

下面的 SQL 语句创建一个名为 "my_db" 的数据库：

```create
CREATE DATABASE my_db;
```

### 2. CREATE TABLE 实例

现在我们想要创建一个名为 "Persons" 的表，包含五列：PersonID、LastName、FirstName、Address 和 City。

我们使用下面的 CREATE TABLE 语句：

```create
CREATE TABLE Persons
(
PersonID int,
LastName varchar(255),
FirstName varchar(255),
Address varchar(255),
City varchar(255)
);
```

### 3. NOT NULL 约束

NOT NULL 约束强制列不接受 NULL 值。

```null
CREATE TABLE Persons (
    ID int NOT NULL,
    LastName varchar(255) NOT NULL,
    FirstName varchar(255) NOT NULL,
    Age int
);
```

在一个已创建的表的 "Age" 字段中添加 NOT NULL 约束如下所示：

```null
ALTER TABLE Persons
MODIFY Age int NOT NULL;
```

在一个已创建的表的 "Age" 字段中删除 NOT NULL 约束如下所示：

```null
ALTER TABLE Persons
MODIFY Age int NULL;
```

### 4. UNIQUE 约束

UNIQUE 约束唯一标识数据库表中的每条记录。

下面的 SQL 在 "Persons" 表创建时在 "P_Id" 列上创建 UNIQUE 约束：

```unique
CREATE TABLE Persons
(
P_Id int NOT NULL,
LastName varchar(255) NOT NULL,
FirstName varchar(255),
Address varchar(255),
City varchar(255),
UNIQUE (P_Id)
)
```

当表已被创建时，如需在 "P_Id" 列创建 UNIQUE 约束，请使用下面的 SQL：

```unique
ALTER TABLE Persons
ADD UNIQUE (P_Id)
```

如需撤销 UNIQUE 约束，请使用下面的 SQL：

```unique
ALTER TABLE Persons
DROP INDEX uc_PersonID
```

### 5. PRIMARY KEY 约束

> 1. PRIMARY KEY 约束唯一标识数据库表中的每条记录。
> 2. 主键必须包含唯一的值。
> 3. 主键列不能包含 NULL 值。
> 4. 每个表都应该有一个主键，并且每个表只能有一个主键。

下面的 SQL 在 "Persons" 表创建时在 "P_Id" 列上创建 PRIMARY KEY 约束：

MySQL：

```key
CREATE TABLE Persons
(
P_Id int NOT NULL,
LastName varchar(255) NOT NULL,
FirstName varchar(255),
Address varchar(255),
City varchar(255),
PRIMARY KEY (P_Id)
)
```

当表已被创建时，如需在 "P_Id" 列创建 PRIMARY KEY 约束，请使用下面的 SQL：

```key
ALTER TABLE Persons
ADD PRIMARY KEY (P_Id)
```

如需撤销 PRIMARY KEY 约束，请使用下面的 SQL：

```key
ALTER TABLE Persons
DROP PRIMARY KEY
```

### 6. FOREIGN KEY 约束

一个表中的 FOREIGN KEY 指向另一个表中的 UNIQUE KEY(唯一约束的键)。

下面的 SQL 在 "Orders" 表创建时在 "P_Id" 列上创建 FOREIGN KEY 约束：

MySQL：

```key
CREATE TABLE Orders
(
O_Id int NOT NULL,
OrderNo int NOT NULL,
P_Id int,
PRIMARY KEY (O_Id),
FOREIGN KEY (P_Id) REFERENCES Persons(P_Id)
)
```

当 "Orders" 表已被创建时，如需在 "P_Id" 列创建 FOREIGN KEY 约束，请使用下面的 SQL：

```key
ALTER TABLE Orders
ADD FOREIGN KEY (P_Id)
REFERENCES Persons(P_Id)
```

如需撤销 FOREIGN KEY 约束，请使用下面的 SQL：

```key
ALTER TABLE Orders
DROP FOREIGN KEY fk_PerOrders
```

### 7.  CHECK 约束

> 1. CHECK 约束用于限制列中的值的范围。
> 2. 如果对单个列定义 CHECK 约束，那么该列只允许特定的值。
> 3. 如果对一个表定义 CHECK 约束，那么此约束会基于行中其他列的值在特定的列中对值进行限制。

下面的 SQL 在 "Persons" 表创建时在 "P_Id" 列上创建 CHECK 约束。CHECK 约束规定 "P_Id" 列必须只包含大于 0 的整数。

```check
CREATE TABLE Persons
(
P_Id int NOT NULL,
LastName varchar(255) NOT NULL,
FirstName varchar(255),
Address varchar(255),
City varchar(255),
CHECK (P_Id>0)
)
```

当表已被创建时，如需在 "P_Id" 列创建 CHECK 约束，请使用下面的 SQL：

```check
ALTER TABLE Persons
ADD CHECK (P_Id>0)
```

如需撤销 CHECK 约束，请使用下面的 SQL：

```check
ALTER TABLE Persons
DROP CONSTRAINT chk_Person
```

### 8. DEFAULT 约束

DEFAULT 约束用于向列中插入默认值。

如果没有规定其他的值，那么会将默认值添加到所有的新记录。

下面的 SQL 在 "Persons" 表创建时在 "City" 列上创建 DEFAULT 约束：

```default
CREATE TABLE Persons
(
    P_Id int NOT NULL,
    LastName varchar(255) NOT NULL,
    FirstName varchar(255),
    Address varchar(255),
    City varchar(255) DEFAULT 'Sandnes'
)
```

当表已被创建时，如需在 "City" 列创建 DEFAULT 约束，请使用下面的 SQL：

MySQL：

```default
ALTER TABLE Persons
ALTER City SET DEFAULT 'SANDNES'
```

如需撤销 DEFAULT 约束，请使用下面的 SQL：

MySQL：

```default
ALTER TABLE Persons
ALTER City DROP DEFAULT
```

### 9. CREATE INDEX 语句

CREATE INDEX 语句用于在表中创建索引。

在不读取整个表的情况下，索引使数据库应用程序可以更快地查找数据。

下面的 SQL 语句在 "Persons" 表的 "LastName" 列上创建一个名为 "PIndex" 的索引：

```index
CREATE INDEX PIndex
ON Persons (LastName)
```

如果您希望索引不止一个列，您可以在括号中列出这些列的名称，用逗号隔开：

```index
CREATE INDEX PIndex
ON Persons (LastName, FirstName)
```

### 10. AUTO INCREMENT 字段

我们通常希望在每次插入新记录时，自动地创建主键字段的值。

我们可以在表中创建一个 auto-increment 字段。

下面的 SQL 语句把 "Persons" 表中的 "ID" 列定义为 auto-increment 主键字段：

```auto

// 用于 MySQL 的语法

CREATE TABLE Persons
(
ID int NOT NULL AUTO_INCREMENT,
LastName varchar(255) NOT NULL,
FirstName varchar(255),
Address varchar(255),
City varchar(255),
PRIMARY KEY (ID)
)
```

下面的 SQL 语句把 "Persons" 表中的 "ID" 列定义为 auto-increment 主键字段：

```auto

// 用于 SQL Server 的语法

CREATE TABLE Persons
(
ID int IDENTITY(1,1) PRIMARY KEY,
LastName varchar(255) NOT NULL,
FirstName varchar(255),
Address varchar(255),
City varchar(255)
)
```
