# Alter 语法

ALTER TABLE 语句用于在已有的表中添加、删除或修改列。

## 演示数据库Persons

| P_Id | LastName         | FirstName                       | Address | City |
-|-|-|-|-|
| 1  | Hansen1       |Ola1    |Timoteivn 10    | Sandnes     |
| 2  | Hansen2       |Ola2    |Timoteivn 10    | Sandnes     |
| 3  | Hansen3      |Ola3    |Timoteivn 10    | Sandnes     |

## 语法

### 1. 添加列

现在，我们想在 "Persons" 表中添加一个名为 "DateOfBirth" 的列。

我们使用下面的 SQL 语句：

``` alter
ALTER TABLE Persons
ADD DateOfBirth date
```

### 2. 改变列

现在，我们想要改变 "Persons" 表中 "DateOfBirth" 列的数据类型。

我们使用下面的 SQL 语句：

```alter
ALTER TABLE Persons
ALTER COLUMN DateOfBirth year
```

### 3. 删除列

接下来，我们想要删除 "Person" 表中的 "DateOfBirth" 列。

我们使用下面的 SQL 语句：

```alter
ALTER TABLE Persons
DROP COLUMN DateOfBirth
```
