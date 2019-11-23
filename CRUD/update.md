# Update 语法

UPDATE 语句用于更新表中已存在的记录。

## 演示数据库Websites

| id | name         | url                       | alexa | country |
-|-|-|-|-|
| 1  | Google       | https://www.google.cm/    | 1     | USA     |
| 2  | 淘宝          | https://www.taobao.com/   | 13    | CN      |
| 3  | 菜鸟教程      | http://www.runoob.com/    | 4689  | CN      |
| 4  | 微博          | http://weibo.com/         | 20    | CN      |
| 5  | Facebook     | https://www.facebook.com/ | 3     | USA     |

## 语法

### 1. UPDATE 实例

```update
UPDATE Websites
SET alexa='5000', country='USA'
WHERE name='菜鸟教程';

执行以下代码会将 Websites 表中所有数据的 alexa 改为 5000，country 改为 USA。
UPDATE Websites
SET alexa='5000', country='USA'
```
