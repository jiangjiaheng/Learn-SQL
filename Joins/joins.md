# Join 语法

SQL join 用于把来自两个或多个表的行结合起来。

## 演示数据库 Websites

| id | name         | url                       | alexa | country |
-|-|-|-|-|
| 1  | Google       | https://www.google.cm/    | 1     | USA     |
| 2  | 淘宝          | https://www.taobao.com/   | 13    | CN      |
| 3  | 菜鸟教程      | http://www.runoob.com/    | 4689  | CN      |
| 4  | 微博          | http://weibo.com/         | 20    | CN      |
| 5  | Facebook     | https://www.facebook.com/ | 3     | USA     |
| 7  | stackoverflow | http://stackoverflow.com/ |   0 | IND     |

下面是 "access_log" 网站访问记录表的数据：

| aid | site_id | count | date       |
-|-|-|-|
|   1 |       1 |    45 | 2016-05-10 |
|   2 |       3 |   100 | 2016-05-13 |
|   3 |       1 |   230 | 2016-05-14 |
|   4 |       2 |    10 | 2016-05-14 |
|   5 |       5 |   205 | 2016-05-14 |
|   6 |       4 |    13 | 2016-05-15 |
|   7 |       3 |   220 | 2016-05-15 |
|   8 |       5 |   545 | 2016-05-16 |
|   9 |       3 |   201 | 2016-05-17 |

## 语法

### 1. INNER JOIN 实例

下面的 SQL 语句将返回所有网站的访问记录：

```join
SELECT Websites.name, access_log.count, access_log.date
FROM Websites
INNER JOIN access_log
ON Websites.id=access_log.site_id
ORDER BY access_log.count;
```

### 2. LEFT JOIN 实例

下面的 SQL 语句将返回所有网站及他们的访问量（如果有的话）。
以下实例中我们把 Websites 作为左表，access_log 作为右表：

```实例
SELECT Websites.name, access_log.count, access_log.date
FROM Websites
LEFT JOIN access_log
ON Websites.id=access_log.site_id
ORDER BY access_log.count DESC;
```

### 3. RIGHT JOIN 实例

下面的 SQL 语句将返回网站的访问记录。
以下实例中我们把 access_log 作为左表，Websites 作为右表：

```实例
SELECT Websites.name, access_log.count, access_log.date
FROM access_log
RIGHT JOIN Websites
ON access_log.site_id=Websites.id
ORDER BY access_log.count DESC;
```

### 4. FULL OUTER JOIN 实例

下面的 SQL 语句选取所有网站访问记录。
MySQL中不支持 FULL OUTER JOIN，你可以在 SQL Server 测试以下实例。

```实例
SELECT Websites.name, access_log.count, access_log.date
FROM Websites
FULL OUTER JOIN access_log
ON Websites.id=access_log.site_id
ORDER BY access_log.count DESC;
```
