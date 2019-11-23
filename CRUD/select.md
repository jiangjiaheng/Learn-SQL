# Select 语法

SELECT 语句用于从数据库中选取数据。结果被存储在一个结果表中，称为结果集。

<!-- TOC -->

- [Select 语法](#select-语法)
    - [演示数据库Websites](#演示数据库websites)
    - [语法](#语法)
        - [1. SELECT Column 实例](#1-select-column-实例)
        - [2. SELECT * 实例](#2-select--实例)
        - [3. SELECT DISTINCT 实例](#3-select-distinct-实例)
        - [4. WHERE 子句实例](#4-where-子句实例)
        - [5. AND 运算符实例](#5-and-运算符实例)
        - [6. OR 运算符实例](#6-or-运算符实例)
        - [7. 结合 AND & OR](#7-结合-and--or)
        - [8. ORDER BY 实例](#8-order-by-实例)
        - [9. ORDER BY DESC 实例](#9-order-by-desc-实例)
        - [10. SELECT TOP 子句](#10-select-top-子句)
        - [11. 列的别名实例](#11-列的别名实例)
        - [12. 表的别名实例](#12-表的别名实例)

<!-- /TOC -->

## 演示数据库Websites

| id | name         | url                       | alexa | country |
-|-|-|-|-|
| 1  | Google       | https://www.google.cm/    | 1     | USA     |
| 2  | 淘宝          | https://www.taobao.com/   | 13    | CN      |
| 3  | 菜鸟教程      | http://www.runoob.com/    | 4689  | CN      |
| 4  | 微博          | http://weibo.com/         | 20    | CN      |
| 5  | Facebook     | https://www.facebook.com/ | 3     | USA     |

## 语法

### 1. SELECT Column 实例

```select
SELECT name,country FROM Websites;
```

### 2. SELECT * 实例

```select
SELECT * FROM Websites;
```

### 3. SELECT DISTINCT 实例

```select
SELECT DISTINCT country FROM Websites;
```

### 4. WHERE 子句实例

```select
SELECT * FROM Websites WHERE country='CN';

SELECT * FROM Websites WHERE id=1;
```

### 5. AND 运算符实例

```select
SELECT * FROM Websites
WHERE country='CN'
AND alexa > 50;
```

### 6. OR 运算符实例

```select
SELECT * FROM Websites
WHERE country='USA'
OR country='CN';
```

### 7. 结合 AND & OR

```select
SELECT * FROM Websites
WHERE alexa > 15
AND (country='CN' OR country='USA');
```

### 8. ORDER BY 实例

```select
SELECT * FROM Websites
ORDER BY alexa;
```

### 9. ORDER BY DESC 实例

```select
SELECT * FROM Websites
ORDER BY country,alexa;
```

### 10. SELECT TOP 子句

```select
SQL Server / MS Access 语法
SELECT TOP number|percent column_name(s)
FROM table_name;

MySQL SELECT LIMIT 实例
SELECT * FROM Websites LIMIT 2;

以下操作在 Microsoft SQL Server 数据库中可执行
SELECT TOP 50 PERCENT * FROM Websites;
```

### 11. 列的别名实例

```select
SELECT name AS n, country AS c
FROM Websites;
```

### 12. 表的别名实例

```select
SELECT w.name, w.url, a.count, a.date
FROM Websites AS w, access_log AS a
WHERE a.site_id=w.id and w.name="菜鸟教程";
```
