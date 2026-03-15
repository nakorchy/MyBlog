---
title: SQL基础语句
published: 2026-03-06
description: ''
image: ''
tags: [SQL]
category: 'Learning'
draft: false 
lang: ''
---

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

&nbsp;
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
```

## 3. 修改记录
```sql
-- 不带条件的修改（修改所有行)
update 表名 set 列名 = 值;

-- 带条件的修改
update 表名 set 列名 = 值 where 列名 = 值;
```

&nbsp;
# DQL 数据查询语言
## 1. 基础关键字
```sql
-- 1. between···and 和 in
--    查询年龄大于等于20，小于等于30
select * from student where age >= 20 && age <=30;
select * from student where age >= 20 and age <=30;
select * from student where age between 20 and 30;

--    查询年龄22，18，25岁的信息
select * from student where age = 22 or age = 18 or age =25;
select * from student where age in (22,18,25);

-- 2. is not null 与like（模糊查询）、distinct（去除重复值）
--    查询英语成绩不为null
select * from student where English is not null

--    _：单个任意字符
--    %：多个任意字符
--    查询姓马的有哪些
select * from student where name like '马%';

--    查询姓名第二个字是一的人
select * from student where name like '_一%';

--    查询姓名是三个字的人
select * from student where name like '___'

--    查询姓名中包含二的人
select * from student where name like '%二'

-- 3. 关键词 distinct 用于返回唯一不同的值
select distinct name from student;
```

## 2. 排序查询 order by
```sql
-- 默认升序
select * from student order by math;

-- 默认降序
select * from student order by math desc;
```