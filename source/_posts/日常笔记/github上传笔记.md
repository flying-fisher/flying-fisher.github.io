---
title: github上传笔记
date: 2018-3-20 20：10：12
tags: 
- github
categories: 
- python
---
 
# <center>Github上传本地文档笔记</center>
## 分三步：
- 1.git add .(后面的点代表是要上传全部文件，如果上传一个文件，可以修改成文件名字)
- 2.git commit -m "说明上传的理由"
- 3.git push -u origin master(如果前面出现错误了，输入后者代码git pull --rebase origin master，然后再重新输入前面的代码)

# <center>ubuntu上安装shadowsocks的方法</center>
- 在ubuntu的终端上，输入下面代码：
```
sudo add-apt-repository ppa:hzwhuang/ss-qt5
sudo apt-get update
sudo apt-get install shadowsocks-qt5

```
然后去软件管理器中调出shadowsocks,里面的设置进行输入即可

## 心形python代码
```python
import time
words = input('Please input the words you want to say!:')
for item in words.split():
    print('\n'.join([''.join([(item[(x-y) % len(item)] if ((x*0.05)**2+(y*0.1)**2-1)**3-(x*0.05)**2*(y*0.1)**3 <= 0 else ' ') for x in range(-30, 30)]) for y in range(12, -12, -1)]))
    time.sleep(1.5)

```