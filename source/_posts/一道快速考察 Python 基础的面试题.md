---
title: 一道快速考察 Python 基础的面试题
date: 2020-03-30 20:02:18
abbrlink: 1273f6f1
index_img: https://static.zkqiang.cn/images/20200208131253.png-cover
tags: [Python, 刷题]
categories:
- 转载
---

>这是前一阵子群友发在群里的一道面试题，利用 Python 字典的特性，可以巧妙地使用精简代码达成完美解。

## 题目

将 data 转换成 new_data 这种形式，写出转换过程。

```python
data = {
    'a_b_h':1,
    'a_b_i':2,
    'a_c_j':3,
    'a_d':4,
    'a_c_k':5,
    'a_e':6
}

new_data = {
    'a':{
        'b':{
            'h':1,
            'i':2
        },
        'c':{
            'j':3,
            'k':5
        },
        'd':4,
        'e':6
    }
}
```

可以看出，转换的过程是将 key 的下划线进行拆分，然后下划线后边的字符嵌套在前面字符的值中。

感兴趣就打开 IDE，自己先试着解一下。

## 解题思路

你应该很快想到，主要思路是将下划线 `split` 后，然后依次使用字符生成内层字典，当达到最后一个字符时将数字作为值。

那么关键点在于，如何不断地获得内层字典去修改呢？实际本题就是考察你是否理解 Python 字典是**引用传递**这个特性。

什么是引用传递？我们知道 Python 中**字典和列表对象都是可变对象**，同一个字典对象的变量不管如何传递，只要改变其中一个变量会同步修改其他变量。这是因为变量存储的只是可变对象的引用，无论调用哪个变量，返回的依然是同一个对象。比如：

```python
new_data = {}
tmp = {}
new_data['a'] = tmp
print(new_data)  # {'a': {}}
tmp['b'] = 1
print(new_data)  # {'a': {'b': 1}}
```

如上，利用这个特性，将内层字典赋值给一个中间变量，然后改变这个中间变量，即可同步修改最终的 new_data 变量。

根据这个思路，初步代码如下：

```python
data = {
    'a_b_h':1,
    'a_b_i':2,
    'a_c_j':3,
    'a_d':4,
    'a_c_k':5,
    'a_e':6
}

new_data = {}

for key, value in data.items():
    keys = key.split('_')
    tmp = new_data
    last = len(keys) - 1  # 最后一个 key 的索引值 
    for i, k in enumerate(keys):
        if i == last:
            tmp[k] = value
            continue
        if k not in tmp:
            sub_tmp = {}
            tmp[k] = sub_tmp
            tmp = sub_tmp
        else:
            tmp = tmp[k]
```

这也是群友给出的第一版答案，这样写并没有多大问题，但是代码比较繁琐，肯定还有优化空间。

我们可以只使用一个中间变量即可，进一步优化：

```python
for field, value in data.items(): 
    keys = field.split('_') 
    tmp = new_data 
    last = len(keys) - 1
    for i, k in enumerate(keys): 
        if k not in tmp:
            tmp[k] = {} if i < last else value
        tmp = tmp[k]  # 将内层 dict 传给 tmp
```

上面这个代码看似很简洁了，但是仍然还有两个 if 判断，如果不是使用了三元表达式的话，还会更多行。

所以可以进一步优化：

```python
for field, value in data.items(): 
    keys = field.split('_') 
    tmp = new_data 
    for k in keys[:-1]: 
        tmp = tmp.setdefault(k, {})
    tmp[keys[-1]] = value
```

我们省略掉了 last 来判断最后一个字符的索引，直接通过 `keys[:-1]` 避开最后一个字符，末尾再单独生成数字键值对。

这里还使用字典的一个内置方法 —— `setdefault`。

`dict.setdefault(key, default=None)` 方法和 `get` 方法类似，只是如果键不存在于字典中，不仅会返回 default 参数的值，还同时会用该值自动生成一个键值对。

```python
if k not in tmp:
    tmp[k] = {}
v = tmp[k]

# 等价于

v = tmp.setdefault(k, {})
```

最终我们使用了 6 行代码就解出该题，这也是接近最简代码。

如果使用字典引用的特性是合格分的话，那么当你用出 `setdefault` 这个方法后，面试官已经给你打了优秀，因此**一定要熟悉基础数据对象的所有内置方法**。


> **转载声明**
>
> **作者**：张凯强
> **原文链接**：https://zkqiang.cn/posts/1273f6f1/
> **作者简介**： 后端开发 / 游戏爱好者 / 巴萨球迷