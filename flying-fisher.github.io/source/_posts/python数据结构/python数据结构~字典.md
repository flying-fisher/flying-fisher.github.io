---
title: python中字典的循环遍历的两种方式
data：2018-3-22 21:12:55
---

# <center>python中字典的循环遍历的两种方式</center>


## python中字典的循环遍历的两种方式
- 1.只对键的遍历
    - 一个简单的for语句就能循环字典的所有键，就像处理序列一样：
    ```python
    dictionary = { "some_key": "some_value" }
    for key in dictionary:
        print("%s --> %s" %(key, dictionary[key]))
    ```

- 2.对键和值都进行遍历
    - 如果只需要值，可以使用d.values，如果想获取所有的键则可以使用d.keys。

    - 如果想获取键和值d.items方法会将键-值对作为元组返回，for循环的一大好处就是可以循环中使用序列解包。
    - 代码实例
    ```python
    for key, value in d.items():
        print (key, ' value : ', value)

        结果如下：
        name1 value : pythontab
        name2 value : .
        name3 value : com
    ```
    