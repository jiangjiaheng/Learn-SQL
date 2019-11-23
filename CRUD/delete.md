# Delete 语法

DELETE 语句用于删除表中的行。

## 演示数据库Websites

| id | name         | url                       | alexa | country |
-|-|-|-|-|
| 1  | Google       | https://www.google.cm/    | 1     | USA     |
| 2  | 淘宝          | https://www.taobao.com/   | 13    | CN      |
| 3  | 菜鸟教程      | http://www.runoob.com/    | 4689  | CN      |
| 4  | 微博          | http://weibo.com/         | 20    | CN      |
| 5  | Facebook     | https://www.facebook.com/ | 3     | USA     |

## 语法

### 1. DELETE 实例

```insert
DELETE FROM Websites
WHERE name='百度' AND country='CN';

您可以在不删除表的情况下，删除表中所有的行。这意味着表结构、属性、索引将保持不变：
DELETE FROM table_name;
或
DELETE * FROM table_name;
```
