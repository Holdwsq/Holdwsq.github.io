---
layout: post
title:  "Python语法惯例"
categories: Python
tags:  Python  
author: Wsq
---

* content
{:toc}

## Python 惯例
Python开发中惯用的代码使用。
1. 让代码既可以导入也可以被执行。
    ```
    if __name__ == '__main__':
    ```
2. 用下面的方式判断逻辑“真”或“假”。
    ```
    if x:
    if not x:
    ```
    **示例代码**：
    ```
    name = 'jackwang'
    fruits = ['apple', 'banana', 'grape']
    owners = {'1001':'wang', '1002': 'zhang'}
    if name and fruits and owners:
        print('I love fruits')
    ```
3. 善于使用in运算符
    ```
    if x in items: # 包含
    for x in items: # 迭代
    ```
    **示例代码**：
    ```
    name = 'Hi Luo'
    if 'L' in name:
        print('the name has an L in it.')
    ```
4. 用序列构建字符串。

    **示例代码**：
    ```
    chars = ['w', 'a', 'n', 'g']
    name = ''.join(chars)
    print(name) # wang
    ```
5. EAFP 优于LBYL。

    EAFP - Easier to Ask Forgiveness than Permission.
    LBYL - Look Before You Leap.
    
    **示例代码**：
    ```
    d = {'x':'5'}
    try:
        value = int(d['x'])
        print(value)
    except(KeyError, TypeError, ValueError):
        value = None
    ```
6. 使用enumerate进行迭代。
    
    **示例代码**：
    ```
    fruits = ['apple', 'orange', 'banana', 'grape']
    for index, fruit in enumerate(fruits):
        print(index, ':', fruit)
    ```
7. 用生成式生成列表。

    **示例代码**：
    ```
    data = [7, 20 ,9 , 16, 18]
    result = [num * 3 for num in data if num > 10]
    print(result)#[60, 48, 54]
    ```