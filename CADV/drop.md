# Drop 语法

## 语法

### 1. DROP INDEX 语句

用于 MySQL 的 DROP INDEX 语法：

```drop
ALTER TABLE table_name DROP INDEX index_name
```

### 2. DROP TABLE 语句

DROP TABLE 语句用于删除表。

```d
DROP TABLE table_name
```

### 3. DROP DATABASE 语句

DROP DATABASE 语句用于删除数据库。

```d
DROP DATABASE database_name
```

### 4. TRUNCATE TABLE 语句

如果我们仅仅需要删除表内的数据，但并不删除表本身，那么我们该如何做呢？

请使用 TRUNCATE TABLE 语句：

```d
TRUNCATE TABLE table_name
```
