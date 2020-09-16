---
title: Hexo之渲染绕过
author: luckyzmj
coverImg: /medias/banner/7.jpg
top: false
cover: false
toc: true
mathjax: false
summary: 在Hexo部署时会默认渲染source下的所有html页面，但有时候想在Hexo博客上单独自定义html页面或README.md时，却不希望被Hexo渲染。
tags:
  - Hexo
  - 渲染绕过
categories:
  - 博客篇
abbrlink: 17fd92ae
reprintPolicy: cc_by
date: 2020-04-28 00:00:00
img:
password:
---

### 0x001 Hexo 渲染

&emsp;&emsp;在Hexo部署时会默认渲染source下的所有html页面，但有时候想在Hexo博客上单独自定义html页面或README.md时，却不希望被Hexo渲染。因此对某个文件或者目录进行排除渲染是非常必要的。

### 0x002 方法一：font matter

`Hexo`新建网站页面，然后将你的代码直接写入 `index.md` 中

在 `Front matter` 中添加 `layout: false`，此方法适用于单一的纯`HTML`
`CSS` 页面。

```bash
---
title: tools
date: 2020-04-28 00:00:00
type: "tools"
layout: false
---
```

### 0x003 方法二：skip render

在博客根目录下的 `_config.yml`，找到 `skip_render`，大概在32行左右，写入你想要的跳过渲染的路径，注意缩进和空格。


```bash
# 指定目录跳过hexo渲染
skip_render:
  - 'tools/*'
  - 'tools/**'
```

>注释：`tools/*` 表示在目录 `source/fireworks` 下的文件全部跳过渲染，`tools/**` 表示在博客根目录 `source/tools/` 文件夹下的文件全部跳过渲染（例如页面的 js、css 在另一个文件夹中）。

### 0x004 案例：webstack 导航 

`webstack`是一个纯静态的网址导航网站，内容均由`viggo`收集并整理。项目基于`bootstrap`前端框架开发。

![image](https://camo.githubusercontent.com/41111c4c1d9922982f380566e6a2f8415204c52c/687474703a2f2f7777772e776562737461636b2e63632f6173736574732f696d616765732f707265766965772e676966)

- Github：[https://github.com/WebStackPage/WebStackPage.github.io](https://github.com/WebStackPage/WebStackPage.github.io)

在博客根目录 `source/`下新建`tools`，然后新建`index.html`,将`webstack`网页源码全选复制粘贴到里面。

- 本站的webstack源码：[view-source:http://luckyzmj.cn/tools/](view-source:http://luckyzmj.cn/tools/)

>注意：将源码里的部分信息以及跳转链接按照你真实个人博客的环境进行修改。

然后打开博客根目录下配置文件`_config.yml`，找到`skip_render`，做如下修改：

```bash
skip_render:
  - 'tools/*'
  - 'tools/**'
```

最后执行`hexo clean`和`hexo s -g `本地预览，检查无误后`hexo g -d`部署到服务器上即可。


### 参考文章

- https://xiabor.com/2020/04/21/hexo3/#%E5%A6%82%E4%BD%95%E8%B7%B3%E8%BF%87hexo%E7%9A%84%E6%B8%B2%E6%9F%93



