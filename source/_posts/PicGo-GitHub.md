---
title: PicGo+GitHub 图床搭建
author: luckyzmj
coverImg: /medias/banner/7.jpg
top: false
cover: false
toc: true
mathjax: false
summary: 使用 PicGo+jsdelivr+GitHub 打造最稳定可靠的免费图床。
tags:
  - PicGo
  - GitHub图床
categories:
  - 博客篇
abbrlink: 7a46f93c
reprintPolicy: cc_by
date: 2020-03-15 00:00:00
img:
password:
---

### 前言

用GitHub搭建图床，在很久之前我就有了解，但由于市面上有挺多免费的图床，比如我之前一直在用的 路过图床，所以一直懒得动手搭建GitHub图床。一直到前两天我在完善博客的相册时，发现 路过图床 免费版的有这么多限制，比如：每小时限制上传50张图片，每天限制上传100张图片，而且免费版用户的存储容量貌似不过300M，这才意识到有一个自己的GitHub图床是多么重要。

### 0x001 PicGO 介绍

PicGo是一款图片上传工具，目前支持 SM.MS图床、腾讯云COS、GitHub图床、七牛图床、Imgur图床、阿里云OSS、又拍云图床，未来将支持更多图床。

在支持的这些图床中，SM.MS和Imgur有免费版和收费版，免费版的肯定有很多的使用限制，比如每小时限制上传次数，限制用户的上传容量等等；腾讯云COS、阿里云、有拍云都是要收费使用的；七牛云貌似前期使用免费，后期又要收费才能使用，就剩下的GitHub才是免费且最可靠的。

PicGo源项目GitHub地址已给出，但是去GitHub下载速度非常慢，这里额外提供一个蓝奏云的快速下载地址。

- GitHub地址：https://github.com/Molunerfinn/PicGo
- 蓝奏云地址：https://luckyzmj.lanzous.com/id3e0id

### 0x002 GitHub 图床

#### 1. 创建GitHub图床仓库

首先需要有一个登录GitHub的账号，没有的话去[GitHub官网](https://github.com/)注册一个

创建一个新的图床仓库，点击右上角的New repository

![](https://cdn.jsdelivr.net/gh/LuckyZmj/imgbed/posts/20200529155833.png)

填写如下配置信息，然后Create创建仓库

![](https://cdn.jsdelivr.net/gh/LuckyZmj/imgbed/posts/20200529160010.png)

#### 2. 获取GitHub token值

点击右上的头像，选择设置Setting

![](https://cdn.jsdelivr.net/gh/LuckyZmj/imgbed/posts/20200529160727.png)

点击选择Developer settings 

![](https://cdn.jsdelivr.net/gh/LuckyZmj/imgbed/posts/20200529160939.png)

点击 Generate New token

![](https://cdn.jsdelivr.net/gh/LuckyZmj/imgbed/posts/20200529161241.png)

填写如下配置信息，只要勾选repo选项即可，然后页面拉到底部点击Generate token 即可

![](https://cdn.jsdelivr.net/gh/LuckyZmj/imgbed/posts/20200529161716.png)

此时会跳转到带有token的页面，将token值复制记录下来，之后用PicGo绑定GitHub图床时会利用到

![](https://cdn.jsdelivr.net/gh/LuckyZmj/imgbed/posts/20200529162127.png)

### 0x003 PicGo 配置

#### 1. 绑定GitHub图床

首先下载安装好PicGo软件，然后在右列表找到GitHub图床配置

![](https://cdn.jsdelivr.net/gh/LuckyZmj/imgbed/posts/20200529163130.png)

**1. 设定仓库名(必填)：** 

按照“GitHub账户名/仓库名的格式填写”，比如我的是：Luckyzmj/imgbed

**2. 设定分支名(必填)：** 

分支名统一填写“master”

**3. 设定Token(必填)：** 

将之前步骤的Token值复制粘贴到这里

**4. 指定存储路径：** 

这个选项可以为空，如果想将图片上传到仓库的指定目录下，可以填写目录名加/，比如我的imgbed仓库下有个posts文件夹，需设置为 posts/

**5. 设定自定义域名：** 

这里统一用jsdelivr的CDN加速域名，在上传图片后成功后，PicGo会将“自定义域名+上传的图片名”生成的访问链接

```

自定义域名格式：https://cdn.jsdelivr.net/gh/GitHub账户名/仓库名
以我的格式为例：https://cdn.jsdelivr.net/gh/Luckyzmj/imgbed
```

配置完全部信息后，点击 设为默认图床，最后点击确定即可

#### 2. 上传图片到图床

在上传区上传图片，可支持本地图片上传(可多选图片)、剪贴板上传、URL上传等三种方式。上传图片成功后，选择你想要生成的图片链接格式

![](https://cdn.jsdelivr.net/gh/LuckyZmj/imgbed/posts/20200529170555.png)

在图片区，可以看到成功上传的图片，选择相应的图片进行操作即可

![](https://cdn.jsdelivr.net/gh/LuckyZmj/imgbed/posts/20200529170831.png)

#### 3. PicGo 注意事项

如果配置完PicGo后却上传图片失败，可以参考以下方法：

1. 检查自定义域名是否正确
2. 仓库名不要有空格
3. 图片名字不要带有特殊符号，如：%、+、*、空格等
4. 建议开启时间戳重命名，防止图片名字重复
5. 上传图片间歇太短，需在PicGo设置中关闭Server选项
6. PicGo应用不稳定因素，需重启应用

### 参考文章

- https://blog.csdn.net/sunhwee/article/details/100109956
