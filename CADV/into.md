# Into 语法

通过 SQL，您可以从一个表复制信息到另一个表。

SELECT INTO 语句从一个表复制数据，然后把数据插入到另一个新表中。

INSERT INTO SELECT 语句从一个表复制数据，然后把数据插入到一个已存在的表中。

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

### 1. SELECT INTO 实例

创建 Websites 的备份复件：

```s
SELECT *
INTO WebsitesBackup2016
FROM Websites;
```

只复制一些列插入到新表中：

```s
SELECT name, url
INTO WebsitesBackup2016
FROM Websites;
```

只复制中国的网站插入到新表中：

```s
SELECT *
INTO WebsitesBackup2016
FROM Websites
WHERE country='CN';
```

复制多个表中的数据插入到新表中：

```s
SELECT Websites.name, access_log.count, access_log.date
INTO WebsitesBackup2016
FROM Websites
LEFT JOIN access_log
ON Websites.id=access_log.site_id;
```

### 2. INSERT INTO SELECT 实例

复制 "apps" 中的数据插入到 "Websites" 中：

```实例
INSERT INTO Websites (name, country)
SELECT app_name, country FROM apps;
```

只复 QQ 的 APP 到 "Websites" 中：

```实例
INSERT INTO Websites (name, country)
SELECT app_name, country FROM apps
WHERE id=1;
```

## 注意

MySQL 数据库不支持 SELECT ... INTO 语句，但支持 INSERT INTO ... SELECT 。

当然你可以使用以下语句来拷贝表结构及数据：

```s
CREATE TABLE 新表
AS
SELECT * FROM 旧表
```
