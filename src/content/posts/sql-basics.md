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
    sex boolean,
    score double(4,1),
    birthday date,
    class varchar(32),
    duty_id int;
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
insert into student(列名1，列名2，···，列名n) values(值1，值2，···，值n)；

-- 不写列名
insert into student values(值1，值2，···，值n);

-- 插入部分数据
insert into student(列名1，列名2) values(值1，值2);
```

## 2. 删除记录
```sql
-- 删除表中数据
delete from student where 列名 = 值;

-- 删除表中所有数据
delete from student;
```

## 3. 修改记录
```sql
-- 不带条件的修改（修改所有行)
update student set 列名 = 值;

-- 带条件的修改
update student set 列名 = 值 where 列名 = 值;
```

&nbsp;
# DQL 数据查询语言
## 1. 基础关键字
```sql
-- 1. between···and 和 in
--    查询年龄大于等于18，小于等于38
select * from student where age >= 18 && age <=38;
select * from student where age >= 18 and age <=38;
select * from student where age between 18 and 38;

--    查询年龄18，20，22岁的信息
select * from student where age = 18 or age = 20 or age =22;
select * from student where age in (18,20,22);

-- 2. is not null 与like（模糊查询）、distinct（去除重复值）
--    查询英语成绩不为null
select * from student where English is not null;

--    _：单个任意字符
--    %：多个任意字符
--    查询姓张的有哪些
select * from student where name like '张%';

--    查询姓名第二个字是三的人
select * from student where name like '_三%';

--    查询姓名是三个字的人
select * from student where name like '___';

--    查询姓名中包含二的人
select * from student where name like '%二';

-- 3. 关键词 distinct 用于返回唯一不同的值
select distinct name from student;
```

## 2. 排序查询 order by
```sql
-- 默认升序
select * from student order by chinese;

-- 默认降序
select * from student order by chinese desc;
```

## 3. 聚合函数
```sql
count
max
min
sum
avg
```

## 4. 分组查询 group by
```sql
-- 按照性别分组。分别查询男、女同学的语文平均分
select sex,avg(chinese) from student group by sex;

-- 按照性别分组。分别查询男、女同学的语文平均分，人数
select sex,avg(chinese),count(*) from student group by sex;

-- 按照性别分组。分别查询男、女同学的语文平均分，人数 要求：分数低于60分的人，不参与分组
select sex,avg(chinese),count(*) from student where chinese > 60 group by sex;

-- 按照性别分组。分别查询男、女同学的语文平均分，人数 要求：分数低于60分的人，不参与分组，分组之后，人数要大于10
select sex,avg(chinese),count(*) from student where chinese > 60 group by sex having count(*) > 10;
```

## 5. 分页查询
```sql
-- 每页显示6条记录
select * from student limit 0,6;  -- 第一页
select * from student limit 6,6;  -- 第二页
select * from student limit 12,6; -- 第三页
```

## 6. 内连接查询
### 1. 隐式内连接
```sql
-- 查询学生姓名，性别，班级表的名称
select student.name,student.sex,class.name from student,class where student.class = class.id;

select
    t1.name,
    t1.sex,
    t2.name
from
    student t1,
    class t2
where
    t1.class = t2.id;
```

### 2. 显式内连接
```sql
-- 语法
select 字段列表 from 表名1 [inner] join 表名2 on 条件;

-- 例如
select * from student inner join class on student.class = class.id;
select * from student join class on student.class = class.id;
```

## 7. 外连接查询
### 1. 左外链接：查询的是左表所有数据及其交集部分
```sql
--    查询所有学生信息，如果学生有职务，则查询职务，没有职务，则不显示
select t1.*,t2.name from student t1 left join duties t2 on t1.duty_id = t2.id;
```

### 2. 右外连接：查询的是右表所有数据及其交集部分
```sql
select t1.*,t2.name from student t1 right join duties t2 on t1.duty_id = t2.id;
```

## 8. 子查询（嵌套查询）
```sql
-- 查询分数最高的学生
-- 1. 查询最高的分数是多少 700
select max(score) from student；

-- 2. 查询学生信息，并且分数为 700 的
select * from student where student.score = 700;

-- 3. 一条sql就完成这个操作。就是子查询
select * from student where student.score = (select max(score) from student);
```

### 1. 子查询的结果是单行单列的
```sql
select * from student where student.score < (select max(score) from student);
```

### 2. 子查询的结果是多行单列的：用运算符 in 判断
```sql
select * from student where student.duty_id in (select id from duties where name = '学生会' or name = '新媒体中心');
```

### 3. 子查询的结果是多行多列的：子查询作为一张虚拟表参与查询
```sql
select * from duties t1 , (select * from student where student.insert_time > '2020-3-17') t2 where t1.id = t2.duty_id;
```

&nbsp;
# DCL 数据控制语言
## 1. 管理用户
### 1. 添加用户
```sql
create user '用户名@主机名' identified by '密码';
```

### 2. 删除用户
```sql
drop user '用户名@主机名';
```