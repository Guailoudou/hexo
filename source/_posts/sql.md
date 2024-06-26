---
title: sql命令整理
date: 2024-04-02 20:13:24
tags: 笔记
---

### SELECT
查询

常用语法：
```
SELECT [需要查询的内容] FROM <数据库名> WHERE [条件];
SELECT email FROM login WHERE username='admin'

```

### INSERT
插入

常用语法：
```
INSERT INTO <数据库名> (字段1,字段2,字段3) VALUES (值1,值2,值3);
INSERT INTO login (username,password,email) VALUES ('admin','123456','admin@admin.com');
```

### DELETE
删除数据

常用语法：
```
DELETE FROM <数据库名> WHERE [条件];
DELETE FROM login WHERE username='admin';
```

### UPDATE
更新

常用语法：
```
UPDATE <数据库名> SET [需要更新的内容] WHERE [条件];
UPDATE login SET password='123456' WHERE username='admin';
```

### AND & OR
逻辑操作符 AND->&& OR->|| 常用于查询WHERE条件

常用语法：
```
SELECT * FROM login WHERE username='admin' AND password='123456';
SELECT * FROM login WHERE username='admin' OR password='123456';
```

### CREATE
创建表

常用语法：
```
CREATE TABLE <数据库名> (
    <字段1> <数据类型> <约束>,
    ...
);
```

### DROP
删除表

常用语法：
```
DROP TABLE <数据库名>;
DROP TABLE login;
```
### MySQL 数据类型
在 MySQL 中，有三种主要的类型：Text（文本）、Number（数字）和 Date/Time（日期/时间）类型。

> text类型

|数据类型|描述|
|--|--|
|CHAR(size)|保存固定长度的字符串（可包含字母、数字以及特殊字符）。在括号中指定字符串的长度。最多 255 个字符。|
|VARCHAR(size)|保存可变长度的字符串（可包含字母、数字以及特殊字符）。在括号中指定字符串的最大长度。最多 255 个字符。注释：如果值的长度大于 255，则被转换为 TEXT 类型。|
|TINYTEXT|存放最大长度为 255 个字符的字符串。|
|TEXT|存放最大长度为 65,535 个字符的字符串。|
|BLOB|用于 BLOBs（Binary Large OBjects）。存放最多 65,535 字节的数据。|
|MEDIUMTEXT|存放最大长度为 16,777,215 个字符的字符串。|
|MEDIUMBLOB|用于 BLOBs（Binary Large OBjects）。存放最多 16,777,215 字节的数据。|
|LONGTEXT|存放最大长度为 4,294,967,295 个字符的字符串。|
|LONGBLOB|用于 BLOBs (Binary Large OBjects)。存放最多 4,294,967,295 字节的数据。|
|ENUM(x,y,z,etc.)|允许您输入可能值的列表。可以在 ENUM 列表中列出最大 65535 个值。如果列表中不存在插入的值，则插入空值。**注释**：这些值是按照您输入的顺序排序的。可以按照此格式输入可能的值： ENUM('X','Y','Z')|
|SET|与 ENUM 类似，不同的是，SET 最多只能包含 64 个列表项且 SET 可存储一个以上的选择。|

> number类型

|数据类型|描述|
|--|--| 
|TINYINT(size)|带符号-128到127 ，无符号0到255。|
|SMALLINT(size)|带符号范围-32768到32767，无符号0到65535, size 默认为 6。|
|MEDIUMINT(size)|带符号范围-8388608到8388607，无符号的范围是0到16777215。 size 默认为9|
|INT(size)|带符号范围-2147483648到2147483647，无符号的范围是0到4294967295。 size 默认为 11|
|BIGINT(size)|带符号的范围是-9223372036854775808到9223372036854775807，无符号的范围是0到18446744073709551615。size 默认为 20|
|FLOAT(size,d)|带有浮动小数点的小数字。在 size 参数中规定显示最大位数。在 d 参数中规定小数点右侧的最大位数。|
|DOUBLE(size,d)|带有浮动小数点的大数字。在 size 参数中规显示定最大位数。在 d 参数中规定小数点右侧的最大位数。|
|DECIMAL(size,d)|作为字符串存储的 DOUBLE 类型，允许固定的小数点。在 size 参数中规定显示最大位数。在 d 参数中规定小数点右侧的最大位数。|

注意：以上的 size 代表的并不是存储在数据库中的具体的长度，如 int(4) 并不是只能存储4个长度的数字。

实际上int(size)所占多少存储空间并无任何关系。int(3)、int(4)、int(8) 在磁盘上都是占用 4 btyes 的存储空间。就是在显示给用户的方式有点不同外，int(M) 跟 int 数据类型是相同的。

例如：

1、int的值为10 （指定zerofill）
```
int（9）显示结果为000000010
int（3）显示结果为010
```
就是显示的长度不一样而已 都是占用四个字节的空间

> date/time类型
> 
|数据类型|描述|
|--|--| 
|DATE()|日期。格式：YYYY-MM-DD **注释**：支持的范围是从 '1000-01-01' 到 '9999-12-31'|
|DATETIME()	|*日期和时间的组合。格式：YYYY-MM-DD HH:MM:SS **注释**：支持的范围是从 '1000-01-01 00:00:00' 到 '9999-12-31 23:59:59'|
|TIMESTAMP()|*时间戳。TIMESTAMP 值使用 Unix 纪元('1970-01-01 00:00:00' UTC) 至今的秒数来存储。格式：YYYY-MM-DD HH:MM:SS **注释**：支持的范围是从 '1970-01-01 00:00:01' UTC 到 '2038-01-09 03:14:07' UTC|
|TIME()	|时间。格式：HH:MM:SS **注释**：支持的范围是从 '-838:59:59' 到 '838:59:59'|
|YEAR()	|2 位或 4 位格式的年。 **注释**：4 位格式所允许的值：1901 到 2155。2 位格式所允许的值：70 到 69，表示从 1970 到 2069。|

*即便 DATETIME 和 TIMESTAMP 返回相同的格式，它们的工作方式很不同。在 INSERT 或 UPDATE 查询中，TIMESTAMP 自动把自身设置为当前的日期和时间。TIMESTAMP 也接受不同的格式，比如 YYYYMMDDHHMMSS、YYMMDDHHMMSS、YYYYMMDD 或 YYMMDD。

> [数据类型原文](https://www.runoob.com/sql/sql-datatypes.html)