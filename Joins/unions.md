# Union 语法

SQL UNION 操作符合并两个或多个 SELECT 语句的结果。

## 演示数据库 Websites

| id | name         | url                       | alexa | country |
-|-|-|-|-|
| 1  | Google       | https://www.google.cm/    | 1     | USA     |
| 2  | 淘宝          | https://www.taobao.com/   | 13    | CN      |
| 3  | 菜鸟教程      | http://www.runoob.com/    | 4689  | CN      |
| 4  | 微博          | http://weibo.com/         | 20    | CN      |
| 5  | Facebook     | https://www.facebook.com/ | 3     | USA     |
| 7  | stackoverflow | http://stackoverflow.com/ |   0 | IND     |

下面是 "apps" APP 的数据：

| id | app_name   | url                     | country |
-|-|-|-|
|  1 | QQ APP     | http://im.qq.com/       | CN      |
|  2 | 微博 APP | http://weibo.com/       | CN      |
|  3 | 淘宝 APP | https://www.taobao.com/ | CN      |

## 语法

### 1. UNION 实例

下面的 SQL 语句从 "Websites" 和 "apps" 表中选取所有不同的country（只有不同的值）：

```实例
SELECT country FROM Websites
UNION
SELECT country FROM apps
ORDER BY country;
```

### 2. UNION ALL 实例

下面的 SQL 语句使用 UNION ALL 从 "Websites" 和 "apps" 表中选取所有的country（也有重复的值）：

```实例
SELECT country FROM Websites
UNION ALL
SELECT country FROM apps
ORDER BY country;
```

### 3. 带有 WHERE 的 SQL UNION ALL

下面的 SQL 语句使用 UNION ALL 从 "Websites" 和 "apps" 表中选取所有的中国(CN)的数据（也有重复的值）：

```实例
SELECT country, name FROM Websites
WHERE country='CN'
UNION ALL
SELECT country, app_name FROM apps
WHERE country='CN'
ORDER BY country;
```
