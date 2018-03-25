---
title: 浏览器的模拟--Header属性
date: 2018-2-22 21：01：10
tags: 浏览器header
---

# <center>浏览器的模拟--Header属性</center> 
有的时候，我们无法爬取一些网页，会出现403错误，因为这些网页为了防止被人恶意采集其信息所以进行了一些反爬虫的设置。
可以设置一些Header信息，模拟成浏览器去访问这些网站，解决这种问题。

爬取CSDN博客的内容为例：
```python
import urllib.request
url = "http://blog.csdn.net/weiwei_pig/article/details/51178226"
file = urllib.request.urlopen(url)
```
此时会出现403异常，即禁止访问的错误，所以接下来我们需要让爬虫模拟成浏览器。模拟成浏览器可以设置User-Agent信息。通过我寻找到百度的User-agent直接使用：如下
```
User-Agent:Mozilla/5.0 (Windows NT 10.0; WOW64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/55.0.2883.87 Safari/537.36
```
# 方法一：使用build_opener()修改报头 
由于urlopen()不支持一些HTTP的高级功能，所以，我们要修改报头，可以使用urllib.request.build_opener()进行，模拟浏览器的代码如下：
```python
import urllib.request
url = "http://blog.csdn.net/weiwei_pig/article/details/51178226"
headers = ("User-Agent","Mozilla/5.0 (Windows NT 10.0; WOW64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/55.0.2883.87 Safari/537.36")
opener = urllib.request.build_opener()
opener.addheaders = [headers]

data = opener.open(url).read()
```
爬取的内容可以写入文件：
```python
fhandle = open("e:/scrapy_data/3.html","wb")
fhandle.write(data)
fhandle.close()
```

# 方法二：使用add_header()添加报头 
还可以利用urllib.request.Request()下的add_header()实现浏览器的模拟。代码如下：
```python
import urllib.request
url = "http://blog.csdn.net/weiwei_pig/article/details/51178226"
req = urllib.request.Request(url)
req.add_header ("User-Agent","Mozilla/5.0 (Windows NT 10.0; WOW64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/55.0.2883.87 Safari/537.36")
data = urllib.request.urlopen(url).read()
```


# 代理服务器的设置
网上整理好的网址(代理服务器)[http://yum.iqianyue.com/proxy] 中找到很多代理服务器地址。打开网页之后，尽量找到验证时间比较短的。此时，我们可以选择第二个代理IP地址223.153.131.205，对应端口808，完整的格式为：“网址：端口号”，即223.153.131.205：808
用了代理IP地址之后，编写程序如下：
```python
def use_proxy(proxy_addr,url):
    import urllib.request
    proxy = urllib.request.ProxyHandler({'http':proxy_addr})
    opener = urllib.request.build_opener(proxy,urllib.request.HTTPHandler)
    urllib.request.install_opener(opener)
    data = urllib.request.urlopen(url).read().decode('utf-8')
    return data
proxy_addr = "223.153.131.205：808"
data = use_proxy(proxy_addr,"http://www.baidu.xom")
print(len(data))
```