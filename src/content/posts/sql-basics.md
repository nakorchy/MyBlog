---
title: SQL基础语句
published: 2026-03-06
description: ''
image: ''
tags: [SQL]
category: 'Knowledge'
draft: false 
lang: ''
---
#
# DDL 数据定义语言
## 1. 操作库
```sql
-- 创建库
create database db;

-- 创建库是否存在，不存在则创建
create database if not exits db;

-- 查看所有数据库
show databases;

-- 查看某个数据库的定义信息
show create database db;

-- 修改数据库字符信息
alter database db character set utf8;

-- 删除数据库
drop database db;
```

## 2. 操作表
```sql
-- 创建表
create table student(
    id int,
    name varchar(32),
    age int,
    score double(4,1),
    birthday date,
    insert_time timestamp
);

-- 查看表结构
desc student;

-- 查看创建表的SQL语句
show create table student;

-- 修改表名
alter table student rename to students;

-- 添加一列
alter table students add phone varchar(32);

-- 删除列
alter table students drop phone;

-- 删除表
drop table students;
drop table if exists students;
```

#
# DML 数据操作语言
## 1. 添加记录
```sql
-- 写全所有列名
insert into 表名(列名1，列名2，···，列名n) values(值1，值2，···，值n)；

-- 不写列名
insert into 表名 values(值1，值2，···，值n);

-- 插入部分数据
insert into 表名(列名1，列名2) values(值1，值2);
```

## 2. 删除记录
```sql
-- 删除表中数据
delete from 表名 where 列名 = 值;

-- 删除表中所有数据
delete from 表名;