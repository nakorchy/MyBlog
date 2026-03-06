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
