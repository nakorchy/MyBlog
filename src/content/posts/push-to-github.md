---
title: 如何把项目上传到GitHub上
published: 2025-12-22
description: ''
image: ''
tags: ["Github"]
category: Technology
draft: false 
lang: ''
---
#
# 一、前期准备
## 1. 注册GitHub

## 2. 安装Git

## 3. 安装完Git后，打开Git Bash，配置用户信息
```markdown
# 替换为GitHub用户名
git config --global user.name "用户名"

# 替换为GitHub注册邮箱
git config --global user.email "邮箱地址"
```

#
# 二、上传步骤
## 1. 在GitHub中创建远程仓库

## 2. 本地项目初始化
```markdown
# 初始化本地Git仓库（首次执行需要）
git init
```

## 3. 提交项目
```markdown
# 1. 将所有文件添加到暂存区
#    如需忽略不必要的文件（如build目录、日志文件），可创建.gitignore文件
git add .

# 2. 提交文件到本地仓库（注明提交说明）
git commit -m "提交说明"
```

## 4. 关联远程仓库
```markdown
git remote add origin https://github.com/用户名/仓库名.git
```

## 5. 推送项目到GitHub
```markdown
# 首次推送需指定分支（默认主分支为main）
git push -u origin main
```

## 6. 更新推送
```markdown
# 1. 添加修改的文件到暂存区
git add .

# 2. 提交修改（注明更新说明）
git commit -m "更新说明"

# 3. 推送到远程仓库
git push
```