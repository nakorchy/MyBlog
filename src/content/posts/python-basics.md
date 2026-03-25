---
title: Python 基础
published: 2026-03-15
description: 'Python 学习记录（一）'
image: ''
tags: [Python]
category: 'Learning'
draft: false 
lang: ''
---

# 1. 变量、基本数据类型与输入输出
补充：Python f-string 字符串格式化输出
```python
# 通过在字符串前加 f 或 F，并在花括号 {} 中嵌入表达式，运行时会将其替换为对应的值。
num = 20
print(f"num = {num}")
```

# 2. 运算符与表达式

# 3. 流程控制语句
## 1. 选择语句
补充：match...case 语句
1. 匹配字面值

2. 绑定变量
```Python
# 出现变量时，这个变量会尽可能匹配 match 的内容，并且会为这个变量进行赋值
a = input("请输入一个需要匹配的数字：)
match a:
    case b:
        print('变量b被赋值为：',b)
```

1. 约束项（if语句）
```Python
# 在实现 case 匹配项时，可以添加一个 if 语句来作为该 case 的约束项。
print = eval(input("请输入坐标："))
match point:
    case (x,y) if x > y:
        print(x,y,'x大于y')
    case (x,y) if x < y:
        print(x,y,'x小于y')
    case (x,y) if x == y:
        print(x,y,'x等于y')
```

1. 匹配字典
```Python
# 1. 匹配字典时，只匹配 case 中提到的结构，而不管字典中的其他键
d = {1:'alan',2:'andy'}
match d:
    case {1:'alan'}:
        print('匹配成功！')

# 2. 如果想要获取原字典中没有匹配到的键值对，可以使用通配符 ** 进行获取
d = {1:'alan',2:'andy'}
match d:
    case {1:'alan'，**remainder}:
        print(remainder)

# 3. 如果想要匹配字典中键值对的值，可以使用变量进行匹配
d = {1:'alan',2:'andy'}
match d:
    case {1:a,2:b}:
        print(a,b)
```

5. 类模式匹配


# 4. 列表和元组
## 4.1 序列
## 4.2 列表
## 4.3 元组

# 5. 字典和集合

# 6. 字符串
