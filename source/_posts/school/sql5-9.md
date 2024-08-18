---
title: 数据库5-9课堂练习
date: 2024-05-09 14:39:29
tags:
hidden: true
---
- [实验-多表连接.docx](实验-多表连接.docx)
- [orderdb.sql](orderdb.sql)

连接所有表
```sql
FROM ordermaster om 
JOIN customer c ON c.customerNo=om.customerNo 
JOIN orderdetail od ON od.orderNo=om.orderNo 
JOIN product p ON p.productNo=od.productNo
JOIN employee e ON e.employeeNo=om.salerNo
```

1.
```sql
SELECT e.employeeNo,e.employeeName,e.address,om.orderNo,om.customerNo,om.orderDate 
FROM employee e JOIN ordermaster om ON e.employeeNo=om.salerNo
WHERE e.address LIKE '上海市%'
ORDER BY om.customerNo DESC
```
2.
```sql
SELECT om.customerNO,c.customerName,om.orderNo,od.quantity,om.orderSum
FROM ordermaster om 
JOIN customer c ON c.customerNo=om.customerNo 
JOIN orderdetail od ON od.orderNo=om.orderNo 
JOIN product p ON p.productNo=od.productNo
WHERE p.productName='32M DRAM';
```
3.
```sql
SELECT e.employeeName,e.department,e.sex,e.birthday
FROM employee e
WHERE e.department IN (
	SELECT department FROM employee WHERE employeeName='张小梅'
)
ORDER BY department DESC;
```
4.
```sql
SELECT e.employeeNo,e.employeeName,e.department,om.orderNo,c.customerName,om.orderDate
FROM ordermaster om 
JOIN customer c ON c.customerNo=om.customerNo 
JOIN employee e ON e.employeeNo=om.salerNo
ORDER BY e.employeeNo DESC;
```
5.
```sql
SELECT od.productNo,p.productName,od.quantity,od.price
FROM orderdetail od
JOIN product p ON p.productNo=od.productNo
WHERE od.quantity>4;
```
6.
```sql
SELECT om.customerNo,c.customerName,od.productNo,p.productName,od.quantity,od.price,om.orderSum
FROM ordermaster om 
JOIN customer c ON c.customerNo=om.customerNo 
JOIN orderdetail od ON od.orderNo=om.orderNo 
JOIN product p ON p.productNo=od.productNo
```
7.
```sql
SELECT e.employeeName,e.department FROM employee e
ORDER BY e.department
```
8.
```sql
SELECT e.employeeName,e.sex,om.orderDate,od.quantity,om.orderSum
FROM ordermaster om 
JOIN orderdetail od ON od.orderNo=om.orderNo 
JOIN employee e ON e.employeeNo=om.salerNo
JOIN product p ON p.productNo=od.productNo
WHERE p.productName='52倍速光驱';
```
9.
```sql
SELECT * --我不知道你要啥啊
FROM ordermaster om 
JOIN orderdetail od ON od.orderNo=om.orderNo 
JOIN employee e ON e.employeeNo=om.salerNo
WHERE e.employeeName='张小娟';
```
...没写完.......