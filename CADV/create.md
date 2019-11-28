# Create 语法

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
