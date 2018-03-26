---
title: Markdown
date: 2018-03-26 12:24:47
tags:
---
# <center>Markdown</center> #
# <center>一级标题</center> #
## 二级标题 ##
### 三级标题 ###

- 我的第一行 
* 我的第二行
> 我一直在使用引用 

> 从现在开始

[Baidu](http://baidu.com)

[美景图片](http://image.so.com/v?q=%E7%BE%8E%E6%99%AF&cmsid=7dc8b5dfb7db1ca53dec66ab145a4d64&cmran=0&cmras=0&i=0&cmg=f30ec52fc98b50534d6d334c97d557e8&src=360pic_strong&z=1#q=%E7%BE%8E%E6%99%AF&i=0&src=360pic_strong&z=1&lightboxindex=0&id=d64c9b0b65e4dfb34e57fe1d2631c13f&multiple=0&itemindex=0&dataindex=0&prevsn=0&currsn=0&jdx=0&fsn=60&kn=50&gn=0&cn=0&gsrc=1)

*你好* 

**你好呀**

# 表格

<table>
    <tr>
        <td>第一组</td>
        <td>一班</td>
    </tr>
    <tr>
        <td>第二组</td>
        <td>二班</td>
    </tr>
</table>

\\

\`

\*

\-

\{你好}

\[hello!]

\(呀呀呀)

\#

\+-*/

```python
import re
import requests
import time

contents = requests.get('https://book.douban.com/latest?icn=index-latestbook-all').text
pattern = re.compile('<li.*?detail-frame.*?href=.*?>(.*?)</a>.*?color-gray">(.*?)</p>',re.S)

resulta = re.findall(pattern,contents)
print(resulta)
for resultas in resulta:
    name,year = resultas
    year = re.sub('\s','',year)
    print(name,year)
    time.sleep(1)

```