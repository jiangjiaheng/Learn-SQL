# Conditions 语法

## 演示数据库 Websites

| id | name         | url                       | alexa | country |
-|-|-|-|-|
| 1  | Google       | https://www.google.cm/    | 1     | USA     |
| 2  | 淘宝          | https://www.taobao.com/   | 13    | CN      |
| 3  | 菜鸟教程      | http://www.runoob.com/    | 4689  | CN      |
| 4  | 微博          | http://weibo.com/         | 20    | CN      |
| 5  | Facebook     | https://www.facebook.com/ | 3     | USA     |
| 7  | stackoverflow | http://stackoverflow.com/ |   0 | IND     |

## 语法

### 1. LIKE 操作符

LIKE 操作符用于在 WHERE 子句中搜索列中的指定模式。

```like
# 下面的 SQL 语句选取 name 以字母 "G" 开始的所有客户：

SELECT * FROM Websites
WHERE name LIKE 'G%';
```

### 2. 通配符

在 SQL 中，通配符与 SQL LIKE 操作符一起使用。


通配符 | 描述
-|-|
% | 替代 0 个或多个字符
_ | 替代一个字符
[charlist] | 字符列中的任何单一字符
[^charlist]或[!charlist] | 不在字符列中的任何单一字符

下面的 SQL 语句选取 url 以字母 "https" 开始的所有网站：

```like
SELECT * FROM Websites
WHERE url LIKE 'https%';
```

下面的 SQL 语句选取 url 包含模式 "oo" 的所有网站：

```like
SELECT * FROM Websites
WHERE url LIKE '%oo%';
```

下面的 SQL 语句选取 name 以一个任意字符开始，然后是 "oogle" 的所有客户：

```like
SELECT * FROM Websites
WHERE name LIKE '_oogle';
```

下面的 SQL 语句选取 name 以 "G" 开始，然后是一个任意字符，然后是 "o"，然后是一个任意字符，然后是 "le" 的所有网站：

```like
SELECT * FROM Websites
WHERE name LIKE 'G_o_le';
```

下面的 SQL 语句选取 name 以 "G"、"F" 或 "s" 开始的所有网站：

```like
SELECT * FROM Websites
WHERE name REGEXP '^[GFs]';
```

下面的 SQL 语句选取 name 不以 A 到 H 字母开头的网站：

```like
SELECT * FROM Websites
WHERE name REGEXP '^[^A-H]';
```

### 3. IN 操作符

N 操作符允许您在 WHERE 子句中规定多个值。

下面的 SQL 语句选取 name 为 "Google" 或 "菜鸟教程" 的所有网站：

```in
SELECT * FROM Websites
WHERE name IN ('Google','菜鸟教程');
```

### 4. BETWEEN 操作符

BETWEEN 操作符用于选取介于两个值之间的数据范围内的值。

下面的 SQL 语句选取 alexa 介于 1 和 20 之间的所有网站：

```b
SELECT * FROM Websites
WHERE alexa BETWEEN 1 AND 20;
```

如需显示不在上面实例范围内的网站，请使用 NOT BETWEEN：

```b
SELECT * FROM Websites
WHERE alexa NOT BETWEEN 1 AND 20;
```

下面的 SQL 语句选取 alexa 介于 1 和 20 之间但 country 不为 USA 和 IND 的所有网站：

```b
SELECT * FROM Websites
WHERE (alexa BETWEEN 1 AND 20)
AND country NOT IN ('USA', 'IND');
```

下面的 SQL 语句选取 name 以介于 'A' 和 'H' 之间字母开始的所有网站：

```b
SELECT * FROM Websites
WHERE name BETWEEN 'A' AND 'H';
```

下面的 SQL 语句选取 name 不介于 'A' 和 'H' 之间字母开始的所有网站：

```b
SELECT * FROM Websites
WHERE name NOT BETWEEN 'A' AND 'H';
```
