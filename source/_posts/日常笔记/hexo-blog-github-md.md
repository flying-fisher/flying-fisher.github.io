---
title: hexo_blog_github.md
date: 2018-03-27 16:01:51
tags: 
- github
---

# <center>hexo博客备份到github上</center>
## 问题描述：
- 之前在师兄那里学的建立hexo博客，主要有三个内容需要知道：1.本地仓库文件夹；2.github仓库管理；3.网页博客内容
- 因为自己有一个笔记本，回到寝室之后写了点白天的学习笔记，但是无法上传，导致我只能用U盘拷贝到本地仓库文件夹才能上传博客。之后就在想，如果实验室电脑上本地仓库文件夹丢失或者系统出现问题，导致本地仓库文件夹里的内容丢失，怎么办？那我以前的工作笔记博客岂不是全部丢失？
- 经过跟师兄交流，师兄给了我很大的帮助，跟我讲解了关于github上的知识，最重要的一点就是：可以把本地的母本文件，也就是本地仓库文件夹的内容上传到github中，这样换一个环境就可以直接利用
```
git clone -b hexo http://github.com/username
```
拷贝到这个环境中，然后添加文件就可以直接上传到博客，并且文本不会丢失<br>
<br>
## 操作步骤：
### 主题思路：
- 1.首先是需要建立自己的hexo博客（内容包含本地文件夹，github仓库，网页博客）
- 2.在github账号中，username.github.io仓库中建立另外一个新分支（branch）
- 3.把本地文件夹的内容按照一般的方法上传到hexo分支中，这样就可以把自己书写的笔记博客内容上传到github上，在云端中保存好文件（这里面有一个重要的坑，在所有文件中只能有blog文件夹中存在.git文件才行，因此，删除其他文件夹中所有的.git 文件，这样就可以把所有的文件上传上hexo分支仓库里）
- 4.打开另一个电脑或者另外一个环境（也可以建立一个文件夹），建立一个新文件夹，输入：
```
git clone -b hexo http://github.com/username
```
- 5.这样就可以把内容下载到文件夹中，新建的文件夹中就是你的旧文件中所有文件。
    - 这里需要提前安装npm,hexo模块，Node.js需要自己查询网上下载，进行安装，然后安装hexo模块，安装代码如下：
```
npm install -g hexo-cli
npm install hexo --save
```
- 6.然后再就可以在新文件夹中/source/_posts新建.md文件(这里跟大家说一下，新建文件需要使用指令)，代码如下：
```
hexo new "***.md"
```
这里可以直接进行添加笔记，然后进行上传，主要有以下几点指令：
```
git add . #添加blog文件夹中所有文件暂存下来
git commit -m "explain"
git push -u commit hexo #把暂存的所有文件上传到github中

hexo init #文件hexo初始化
hexo g #hexo generate 生成网页文件
hexo d #hexo deploy 建立在http://username.github.io博客网页上
hexo s #hexo severes 运行在本地服务器上
```
然后打开浏览器输入地址： localhost:4000（这里一般默认端口是4000）
这里的端口可以进行修改，当然如果不知道就去问问度娘，教程很多，自己摸索一下！


此时此刻，自己打开http://username.github.io 试一试内容有没有上传上去，如果觉得写得不是很明确，请来信互相探讨！谢谢观阅本文！