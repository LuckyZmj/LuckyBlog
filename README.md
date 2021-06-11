## Hexo-Blog-Lucky
### demo: www.luckyzmj.cn

=======

### 前言

之前在[B站](https://www.bilibili.com/)上发布了个人博客的视频，播放量也破千了，有网友私聊也想要搭建一个这样的博客。经过一段时间的准备，现将本人博客的源代码公布出来，大家只需要根据以下的步骤，即可快速搭建一个漂亮完善的博客。

![](https://cdn.jsdelivr.net/gh/LuckyZmj/imgbed@master/posts/20210518215948.png)

### 0x01 LuckyBlog 介绍

上一个LuckyBlog版本发布于2020年的9月份，是在 [洪卫の博客](https://sunhwee.com/) 基础上进行修改的。自从发布以来有很多网友都私信搭建了博客，同时也发现了旧版本中存在的一些问题需要解决，例如：搜索框不适配XML代码搜索，部分图片失效，代码块问题以及各种小问题。现在将最新的LuckyBlog版本代码发布出来，修复改进了不少的BUG，使其更加稳定运行。同时完善了博客的基础功能，例如：音乐、视频、相册、百宝箱等页面。同时增加了不少的新功能，例如：适配Hexo5.x、黑白天浏览模式、仿Windows页面，站点统计等。

- 博客演示地址：http://luckyzmj.cn/
- 开源项目地址：https://github.com/LuckyZmj/LuckyBlog

**主题特性**

- [x] 简单漂亮，文章内容美观易读
- [x] [Material Design](https://material.io/) 设计
- [x] 响应式设计，博客在桌面端、平板、手机等设备上均能很好的展现
- [x] 首页轮播文章及每天动态切换 `Banner` 图片
- [x] 瀑布流式的博客文章列表（文章无特色图片时会有 `24` 张漂亮的图片代替）
- [x] 时间轴式的归档页
- [x] `词云`的标签页和`雷达图`的分类页
- [x] 丰富的关于我页面（包括关于我、文章统计图、我的项目、我的技能、相册等）
- [x] 可自定义的数据的友情链接页面
- [x] 支持文章置顶和文章打赏
- [x] 支持 `MathJax`
- [x] `TOC` 目录，优化了目录显示效果
- [x] 可设置复制文章内容时追加版权信息
- [x] 可设置阅读文章时做密码验证
- [x] [Gitalk](https://gitalk.github.io/)、[Gitment](https://imsun.github.io/gitment/)、[Valine](https://valine.js.org/) 和 [Disqus](https://disqus.com/) 评论模块（推荐使用 `Valine`）
- [x] 集成了[不蒜子统计](http://busuanzi.ibruce.info/)、谷歌分析（`Google Analytics`）和文章字数统计等功能
- [x] 支持在首页的音乐播放和视频播放功能
- [x] 修改了原主题以及基础主题中的一些`BUG`
- [x] 加入图片懒加载功能，在根目录配置文件开启和关闭
- [x] 增加`留言板`功能   
- [x] 在关于板块,加入`简历`功能页
- [x] 增加完善`音乐`、`相册`、`视频`等功能页面 
- [x] 支持`emoji`表情，用`markdown emoji`语法书写直接生成对应的能**跳跃**的表情
- [x] 增加网站运行时间显示
- [x] 增加`live2d` 动漫人物模型
- [x] 整体替换Banner图片和文章特色图片
- [x] 增加实用的快捷导航栏功能
- [x] 修改了一些控件的参数以及部分样式
- [x] 优化了代码显示块的效果
- [x] 增加页面樱花飘落动效
- [x] 增加鼠标点击烟花爆炸动效
- [x] 增加页面雪花飘落动效
- [x] 增加博客白云背景效果
- [x] 增加天气接口控件
- [x] 加入鼠标点击文字特效
- [x] 增加`DaoVoice`在线聊天插件
- [x] 增加博客代码、图片压缩功能
- [x] 增加黑白天浏览模式功能
- [x] 增加仿`Windows`功能
- [x] 增加站点统计功能
- [x] 增加留言版一言功能
- [x] 其他

### 0x02 LuckyBlog 安装

#### 1. 安装Git
`Git`是目前世界上最先进的分布式版本控制系统，可以有效、高速的处理从很小到非常大的项目版本管理。`Git`的作用是将本地的网页文件传到`github`上。

- Git[下载地址](https://git-scm.com/download)
- Git[教程](https://www.liaoxuefeng.com/wiki/896043488029600)

**windows：** 到git官网上下载.exe文件,Download git,安装选项全部默认即可。

#### 2. 安装node.js
`Hexo`是基于`node.js`编写的，所以需要安装一下`node.js`和里面的`npm`工具。

**windows：** 到[Node.js官网](http://nodejs.cn/download/)下载`.exe`文件，安装选项全部默认。安装好之后，按`Win+R`打开cmd命令提示符，输入`node -v`和`npm -v`，若出现版本号，则说明安装成功。

#### 3. 添加npm国内源

使用阿里的国内镜像进行加速下载

```bash
npm config set registry https://registry.npm.taobao.org
```

#### 4. 安装Hexo

前面`git`和`nodejs`安装好后，就可以安装`hexo`了，你可以先创建一个文件夹`MyBlog`，用来存放自己的博客文件，然后`cd`到这个文件夹下（或者在这个文件夹下直接鼠标右键`git bash`打开）。

比如我的博客文件都存放在`C:\MyBlog`目录下。

在该目录下右键点击`Git Bash Here`，打开`git`的控制台窗口，以后我们所有的操作都在`git`控制台进行，就不用`Windows`自带的`cmd`了。

定位到该目录下，输入`npm install -g hexo-cli`安装`Hexo`。可能会有几个报错，不用理会。

```bash
npm install -g hexo-cli
```

安装完后输入`hexo -v`验证是否安装成功。

接下来初始化一下`hexo`,即初始化我们的博客网站。例如我的在`C:\MyBlog`文件夹下的命令行中，输入`hexo init`初始化文件夹

```bash
hexo init
```

新建完成后，指定文件夹`MyBlog`目录下有：

- `node_modules`: 依赖包
- `public`：存放生成的页面
- `scaffolds`：生成文章的一些模板
- `source`：用来存放你的文章
- `themes`：主题**
- `_config.yml`: 博客的配置文件**

到此为止，本地的Hexo基础环境搭建完成了。

#### 5. 安装LuckyBlog

下载源代码到本地文件下

```bash
git clone https://github.com/LuckyZmj/LuckyBlog.git
```

将下载好的`LuckyBlog`全部复制到`MyBlog`目录下，如果复制过程中出现重复文件，点击替换。

![](https://cdn.jsdelivr.net/gh/LuckyZmj/imgbed@master/posts/20210518202657.png)


最后使用 `npm i` 或者 `npm install` 安装依赖环境包即可。

>如果安装依赖环境出错，可以参考[这篇文章](https://blog.csdn.net/Seven71111/article/details/103364738)。

最后执行 `hexo clean` 和 `hexo s -g` 启动Hexo本地预览，即可看到效果。

![](https://cdn.jsdelivr.net/gh/LuckyZmj/imgbed@master/posts/20210518204521.JPG)

到此为止LuckyBlog安装完成，接下来就是个性化设置了。

### 0x03 LuckyBlog 个性化

>注意！注意！注意！在阅读以下博客个性化之前，最好希望大家有Hexo博客配置主题的基础。如果是完全小白，建议去网上搜索学习相关Hexo搭建博客的过程，另外去B站上也有很多视频教程。博客个性化是需要大家有耐心的，因为每个人的操作不同，在配置过程中可能会遇到一些不可预期的问题，希望大家可以克服这些困难，如有需要帮助，也可以私信博主帮助大家解决问题。

#### 1. 修改部署平台

编辑根目录下的配置文件`MyBlog/_config.yml`，找到如下内容并修改

```bash
deploy:
- type: git
  repo: git@github.com:LuckyZmj/LuckyZmj.github.io.git # 替换为你的部署平台地址
  branch: master
```

#### 2. 修改网站信息

编辑根目录下的配置文件`MyBlog/_config.yml`，找到如下内容并修改

```bash
# Site
title: Luckey
subtitle: 'Luckeyの博客'  
description: '本科 | 计算机科学与技术 | 网络安全'
keywords: 'luckyzmj 计算机 网络安全 渗透测试'  # 博客网站关键词
author: Luckey   # 博主名称
language: zh-CN
timezone: ''

# URL
## If your site is put in a subdirectory, set url as 'http://example.com/child' and root as '/child/'
url: http://www.luckyzmj.cn   # 更改为你的博客地址
root: /
# permalink: :year/:month/:day/:title/
permalink: posts/:abbrlink.html  # p 是自定义的前缀
abbrlink:
    alg: crc32   #算法： crc16(default) and crc32
    rep: hex     #进制： dec(default) and hex
permalink_defaults:
pretty_urls:
  trailing_index: true # Set to false to remove trailing 'index.html' from permalinks
  trailing_html: true # Set to false to remove trailing '.html' from permalinks
```

#### 3. 修改博客头像

编辑主题目录下的配置文件`MyBlog/themes/matery/_config.yml`，找到如下内容并修改

```bash
# Configure website favicon and LOGO
# 将以下改为自己的头像链接即可
favicon: https://s1.ax1x.com/2020/05/17/YR20js.jpg
logo: https://s1.ax1x.com/2020/05/17/YRWsYT.png
```


#### 4. 修改留言板简介

演示效果如下：

![](https://cdn.jsdelivr.net/gh/LuckyZmj/imgbed@master/posts/20210518204949.png)

编辑 `/MyBlog/contact/index.md`，修改你想要内容即可

```bash
---
title: contact
date: 2019-10-25 00:00:00
type: "contact"
layout: "contact"
---

## 畅所欲言
---
在这里可以留下你的足迹，欢迎在下方留言，欢迎交换友链，一起交流学习！

## 友链
---
Lucky_Meの友链信息

博客名称: Lucky_Meの博客

博客网址: http://luckyzmj.cn

博客头像: https://s1.ax1x.com/2020/05/17/YRWsYT.png

博客介绍: 越努力，越幸运！
```

#### 5. 修改音乐列表

想要修改自己喜欢的音乐之前，需要先获取音乐列表的id。

以QQ音乐为例：先登录[QQ音乐网页版](https://y.qq.com/)，点击打开自己喜欢的音乐列表，在网页的URL处包含了音乐列表的id，如下图所示

![](https://cdn.jsdelivr.net/gh/LuckyZmj/imgbed/posts/20200916213029.png)

编辑主题目录下的配置文件`MyBlog/themes/matery/_config.yml`，找到如下内容并修改

```bash
# 默认是博主的QQ音乐的id，大家可以改为自己音乐喜欢列表的id
# 更新完id，就可以同步加载自己喜欢的列表音乐了

# Whether to display the musics.
# 是否在首页显示音乐.
music:
  enable: true
  title: #非吸底模式有效
    enable: true
    show: 听听音乐
  autoHide: true    # hide automaticaly
  server: tencent   #require  music platform: netease, tencent, kugou, xiami, baidu
  type: playlist    #require song, playlist, album, search, artist
  id: 1776127550     #require song id / playlist id / album id / search keyword
  fixed: true       # 开启吸底模式
  autoplay: false   # 是否自动播放
  theme: '#42b983'
  loop: 'all'       # 音频循环播放, 可选值: 'all', 'one', 'none'
  order: 'random'   # 音频循环顺序, 可选值: 'list', 'random'
  preload: 'auto'   # 预加载，可选值: 'none', 'metadata', 'auto'
  volume: 0.7       # 默认音量，请注意播放器会记忆用户设置，用户手动设置音量后默认音量即失效
  listFolded: true  # 列表默认折叠
  hideLrc: true     # 隐藏歌词

# Whether to display the musics.
# 单独的音乐页面.
musics:
  enable: true
  title:          #非吸底模式有效
    enable: true
    show: 听听音乐
  server: tencent   #require music platform: netease, tencent, kugou, xiami, baidu
  type: playlist    #require song, playlist, album, search, artist
  id: 1776127550     #require song id / playlist id / album id / search keyword
  fixed: false      # 开启吸底模式
  autoplay: true   # 是否自动播放
  theme: '#42b983'
  loop: 'all'       # 音频循环播放, 可选值: 'all', 'one', 'none'
  order: 'random'   # 音频循环顺序, 可选值: 'list', 'random'
  preload: 'auto'   # 预加载，可选值: 'none', 'metadata', 'auto'
  volume: 0.7       # 默认音量，请注意播放器会记忆用户设置，用户手动设置音量后默认音量即失效
  listFolded: false  # 列表默认折叠
  listMaxHeight: "525px" #列表最大高度
```

#### 6. 绑定 Valine 评论

编辑主题目录下的配置文件`MyBlog/themes/matery/_config.yml`，找到如下内容并修改

```bash
# Valine 评论模块的配置，默认为不激活，如要使用，就请激活该配置项，并设置 appId 和 appKey.
valine:
  enable: true
  appId: Ucrxxxxxxxxxxxxxxxx-xxxxsz  # 自行注册valine获取
  appKey: zPsLxxxxxxxxxxxxxxerLmd    # 自行注册valine获取
  notify: true
  verify: true
  visitor: true
  avatar: 'monsterid' # Gravatar style : mm/identicon/monsterid/wavatar/retro/hide
  pageSize: 10
  placeholder: '留下你的足迹..' # Comment Box placeholder
  background: /medias/comment_bg.png
  count: true
  enableQQ: 16463223  # 改为自己的QQ号
  recordIP: true
  requiredFields: 
    - nick
    - mail
  guest_info: 
    - nick
    - mail
    - link
  master: 
    - 46606772953bed0812789d6dc955614e  # md5加密后的博主邮箱
  metaPlaceholder:  # 输入框的背景文字
    nick: 昵称/QQ号(必填)
    mail: 邮箱(必填)
    link: 网址(https://)
  lang: zh-CN
  tagMeta: # The String Array of Words to show Flag.[Just Only xCss Style mode]
    - 博主
    - 小伙伴
    - 访客
  friends: # The MD5 String Array of friends Email to show friends Flag.[Just Only xCss Style mode]
    - cb3e577ff029d6073400d5557effd41f   
    -
```

#### 7. 绑定 DaoVoice 在线聊天

编辑主题目录下的配置文件`MyBlog/themes/matery/_config.yml`，找到如下内容并修改

```bash
daovoice:
  enable: true
  app_id: 4xxxxxxxe   #DaoVoice中的app_id
```

#### 8. 快捷导航页面个性化

编辑文件`MyBlog/source/tools/index.html`，以下简单标记出几处，还有其他涉及到博客信息的内容都需要改为你自己的博客信息即可。

![](https://cdn.jsdelivr.net/gh/LuckyZmj/imgbed/posts/20200916235833.png)

#### 9. 添加友情链接

编辑文件`MyBlog/suorce/_data/friends.json`，按如下格式添加友情

```bash
[
    {
        "avatar": "https://s1.ax1x.com/2020/05/17/YRWsYT.png",
        "name": "Luckey",
        "introduction": "越努力，越幸运",
        "url": "http://www.luckyzmj.cn",
        "title": "访问主页"
    },{
      "avatar": "https://sunhwee.com/hwsun.jpg",
      "name": "洪卫の博客",
      "introduction": "UESTC CVer",
      "url": "http://sunhwee.com",
      "title": "访问主页"
    }
]
```

#### 10. 添加相册

比如你的图片上传图床后，链接地址如下

```bash
https://cdn.jsdelivr.net/gh/LuckyZmj/imgbed/galleries/璀璨星空/01.jpg
https://cdn.jsdelivr.net/gh/LuckyZmj/imgbed/galleries/璀璨星空/02.jpg
https://cdn.jsdelivr.net/gh/LuckyZmj/imgbed/galleries/动漫风景/01.jpg
https://cdn.jsdelivr.net/gh/LuckyZmj/imgbed/galleries/动漫风景/02.jpg
...
```

首先提取出图片链接公共的部分，作为图床地址

```bash
https://cdn.jsdelivr.net/gh/LuckyZmj/imgbed/galleries/
```

然后再提取图片地址中不同的部分，作为图片地址

```bash
璀璨星空/01.jpg
璀璨星空/02.jpg
动漫风景/01.jpg
动漫风景/03.jpg
...
```

>具体怎么分割根据你自己图床的链接格式而定，以上为我的github图床格式为例。

将相册图床的地址改为你自己的图床地址，需要更改两处文件

```bash
# 例如我的图床地址为：
https://cdn.jsdelivr.net/gh/LuckyZmj/imgbed/galleries/
```

themes/matery/layout/galleries.ejs

![](https://cdn.jsdelivr.net/gh/LuckyZmj/imgbed/posts/20201008183019.png)

themes/matery/layout/gallerie.ejs

![](https://cdn.jsdelivr.net/gh/LuckyZmj/imgbed/posts/20201008183219.png)

为每个相册添加链接地址，在根目录/source/List/galleries/下新建 相册名称 文件夹，并在该文件夹下新建 `index.md` 

![](https://cdn.jsdelivr.net/gh/LuckyZmj/imgbed/posts/20201008183808.png)

最后，在根目录/source/_data/galleries.json中添加图片链接，格式如下,

```bash
[
  {
    "name": "璀璨星空",
    "cover": "璀璨星空/01.jpg",
    "description": "璀璨星空",
    "photos": [
      "璀璨星空/01.jpg",
      "璀璨星空/02.jpg",
      "璀璨星空/03.jpg",
      "璀璨星空/04.jpg",
      "璀璨星空/05.jpg",
      "璀璨星空/06.jpg",
      "璀璨星空/07.jpg",
      "璀璨星空/08.jpg",
      "璀璨星空/09.jpg",
      "璀璨星空/10.jpg",
      "璀璨星空/11.jpg",
      "璀璨星空/12.jpg",
      "璀璨星空/13.jpg",
      "璀璨星空/14.jpg",
      "璀璨星空/15.jpg",
      "璀璨星空/16.jpg"
    ]
  },
  {
    "name": "动漫风景",
    "cover": "动漫风景/01.jpg",
    "description": "动漫风景",
    "photos": [
      "动漫风景/01.jpg",
      "动漫风景/02.jpg",
      "动漫风景/03.jpg",
      "动漫风景/04.jpg",
      "动漫风景/05.jpg",
      "动漫风景/06.jpg",
      "动漫风景/07.jpg",
      "动漫风景/08.jpg",
      "动漫风景/09.jpg",
      "动漫风景/10.jpg",
      "动漫风景/11.jpg",
      "动漫风景/12.jpg",
      "动漫风景/13.jpg",
      "动漫风景/14.jpg",
      "动漫风景/15.jpg",
      "动漫风景/16.jpg"
    ]
  }
]
```

#### 11. 站点统计功能

站点统计的数据来源于[百度统计](https://tongji.baidu.com/web/welcome/login),当你的网站被百度收录后就会在百度统计中出现数据，具体效果如下：

![](https://cdn.jsdelivr.net/gh/LuckyZmj/imgbed@master/posts/20210518211242.png)

由于博客的统计页面数据不能直接从百度站点中调用，因此需要自行从百度站点中将相应数据填入博客站点统计页面的源代码文件中，个人建议每隔一个月手动更新一次数据。

打开`MyBlog\themes\matery\layout\census.ejs`文件，将百度统计中的数据填入源代码中，修改代码如下：

![](https://cdn.jsdelivr.net/gh/LuckyZmj/imgbed@master/posts/20210518210629.png)

#### 11. 仿Windows个性化

仿Windows页面是采用[YLUI](https://ylui.yuri2.cn/)实现的，YLUI提供了社区版本供大家学习使用，具体效果如下：

![](https://cdn.jsdelivr.net/gh/LuckyZmj/imgbed@master/posts/20210518211817.png)

大家可以查看YLUI官方的[开发文档](https://github.com/yuri2peter/ylui/tree/master/documents)进行开发，有不懂的可以加官方的QQ群：`191372634` 进行讨论。

#### 12. 博客动漫风格背景图

因为在上一个LuckyBlog版本发布的网站风格是偏向动漫风格的，如果大家喜欢动漫风格，只需要替换以下配置即可。

**博客每日轮播图：** 以下链接图片全部下载保存到`MyBlog\themes\matery\source\medias\banner`中，以0~7.jpg的文件名格式命名即可。

```html
https://cdn.jsdelivr.net/gh/LuckyZmj/LuckyBlog@master/themes/matery/source/medias/banner/0.jpg
https://cdn.jsdelivr.net/gh/LuckyZmj/LuckyBlog@master/themes/matery/source/medias/banner/1.jpg
https://cdn.jsdelivr.net/gh/LuckyZmj/LuckyBlog@master/themes/matery/source/medias/banner/2.jpg
https://cdn.jsdelivr.net/gh/LuckyZmj/LuckyBlog@master/themes/matery/source/medias/banner/3.jpg
https://cdn.jsdelivr.net/gh/LuckyZmj/LuckyBlog@master/themes/matery/source/medias/banner/4.jpg
https://cdn.jsdelivr.net/gh/LuckyZmj/LuckyBlog@master/themes/matery/source/medias/banner/5.jpg
https://cdn.jsdelivr.net/gh/LuckyZmj/LuckyBlog@master/themes/matery/source/medias/banner/6.jpg
https://cdn.jsdelivr.net/gh/LuckyZmj/LuckyBlog@master/themes/matery/source/medias/banner/7.jpg
```

**无文章特色背景图：** 打开主题配置文件`MyBlog\themes\matery\_config.yml`，修改替换如下代码即可：

```bash
# The post featured images that needs to be displayed when there is no image.
# 无文章特色图片时需要显示的文章特色图片.
featureImages: 
- https://cdn.jsdelivr.net/gh/LuckyZmj/imgbed@master/galleries/%E5%8A%A8%E6%BC%AB%E9%A3%8E%E6%99%AF/01.jpg
- https://cdn.jsdelivr.net/gh/LuckyZmj/imgbed@master/galleries/%E5%8A%A8%E6%BC%AB%E9%A3%8E%E6%99%AF/02.jpg
- https://cdn.jsdelivr.net/gh/LuckyZmj/imgbed@master/galleries/%E5%8A%A8%E6%BC%AB%E9%A3%8E%E6%99%AF/04.jpg
- https://cdn.jsdelivr.net/gh/LuckyZmj/imgbed@master/galleries/%E5%8A%A8%E6%BC%AB%E9%A3%8E%E6%99%AF/06.jpg
- https://cdn.jsdelivr.net/gh/LuckyZmj/imgbed@master/galleries/%E5%8A%A8%E6%BC%AB%E9%A3%8E%E6%99%AF/07.jpg
- https://cdn.jsdelivr.net/gh/LuckyZmj/imgbed@master/galleries/%E5%8A%A8%E6%BC%AB%E9%A3%8E%E6%99%AF/10.jpg
- https://cdn.jsdelivr.net/gh/LuckyZmj/imgbed@master/galleries/%E5%8A%A8%E6%BC%AB%E9%A3%8E%E6%99%AF/11.jpg
- https://cdn.jsdelivr.net/gh/LuckyZmj/imgbed@master/galleries/%E5%8A%A8%E6%BC%AB%E9%A3%8E%E6%99%AF/12.jpg
- https://cdn.jsdelivr.net/gh/LuckyZmj/imgbed@master/galleries/%E5%8A%A8%E6%BC%AB%E9%A3%8E%E6%99%AF/09.jpg
- https://cdn.jsdelivr.net/gh/LuckyZmj/imgbed@master/galleries/%E5%8A%A8%E6%BC%AB%E9%A3%8E%E6%99%AF/14.jpg
- https://cdn.jsdelivr.net/gh/LuckyZmj/imgbed@master/galleries/%E5%8A%A8%E6%BC%AB%E9%A3%8E%E6%99%AF/15.jpg
- https://cdn.jsdelivr.net/gh/LuckyZmj/imgbed@master/galleries/%E5%8A%A8%E6%BC%AB%E9%A3%8E%E6%99%AF/16.jpg
- https://cdn.jsdelivr.net/gh/LuckyZmj/imgbed@master/galleries/%E4%BA%8C%E6%AC%A1%E5%85%83%E9%A3%8E/06.jpg
- https://cdn.jsdelivr.net/gh/LuckyZmj/imgbed@master/galleries/%E5%8A%A8%E6%BC%AB%E6%8F%92%E7%94%BB/02.jpg
- https://cdn.jsdelivr.net/gh/LuckyZmj/imgbed@master/galleries/%E5%8A%A8%E6%BC%AB%E6%8F%92%E7%94%BB/03.jpg
- https://cdn.jsdelivr.net/gh/LuckyZmj/imgbed@master/galleries/%E5%8A%A8%E6%BC%AB%E6%8F%92%E7%94%BB/04.jpg
- https://cdn.jsdelivr.net/gh/LuckyZmj/imgbed@master/galleries/%E5%8A%A8%E6%BC%AB%E6%8F%92%E7%94%BB/07.jpg
- https://cdn.jsdelivr.net/gh/LuckyZmj/imgbed@master/galleries/%E5%8A%A8%E6%BC%AB%E6%8F%92%E7%94%BB/08.jpg
- https://cdn.jsdelivr.net/gh/LuckyZmj/imgbed@master/galleries/%E5%8A%A8%E6%BC%AB%E6%8F%92%E7%94%BB/11.jpg
- https://cdn.jsdelivr.net/gh/LuckyZmj/imgbed@master/galleries/%E5%8A%A8%E6%BC%AB%E6%8F%92%E7%94%BB/10.jpg
- https://cdn.jsdelivr.net/gh/LuckyZmj/imgbed@master/galleries/%E5%8A%A8%E6%BC%AB%E6%8F%92%E7%94%BB/09.jpg
- https://cdn.jsdelivr.net/gh/LuckyZmj/imgbed@master/galleries/%E5%8A%A8%E6%BC%AB%E6%8F%92%E7%94%BB/12.jpg
- https://cdn.jsdelivr.net/gh/LuckyZmj/imgbed@master/galleries/%E5%8A%A8%E6%BC%AB%E6%8F%92%E7%94%BB/13.jpg
- https://cdn.jsdelivr.net/gh/LuckyZmj/imgbed@master/galleries/%E5%8A%A8%E6%BC%AB%E6%8F%92%E7%94%BB/14.jpg
- https://cdn.jsdelivr.net/gh/LuckyZmj/imgbed@master/galleries/%E7%92%80%E7%92%A8%E6%98%9F%E7%A9%BA/16.jpg
- https://cdn.jsdelivr.net/gh/LuckyZmj/imgbed@master/galleries/%E7%92%80%E7%92%A8%E6%98%9F%E7%A9%BA/15.jpg
- https://cdn.jsdelivr.net/gh/LuckyZmj/imgbed@master/galleries/%E7%92%80%E7%92%A8%E6%98%9F%E7%A9%BA/11.jpg
- https://cdn.jsdelivr.net/gh/LuckyZmj/imgbed@master/galleries/%E7%92%80%E7%92%A8%E6%98%9F%E7%A9%BA/09.jpg
- https://cdn.jsdelivr.net/gh/LuckyZmj/imgbed@master/galleries/%E7%92%80%E7%92%A8%E6%98%9F%E7%A9%BA/03.jpg
- https://cdn.jsdelivr.net/gh/LuckyZmj/imgbed@master/galleries/%E5%8A%A8%E6%BC%AB%E9%A3%8E%E6%99%AF/08.jpg
- https://cdn.jsdelivr.net/gh/LuckyZmj/imgbed@master/galleries/%E5%8A%A8%E6%BC%AB%E9%A3%8E%E6%99%AF/03.jpg
- https://cdn.jsdelivr.net/gh/LuckyZmj/imgbed@master/galleries/%E5%8A%A8%E6%BC%AB%E9%A3%8E%E6%99%AF/13.jpg
- https://cdn.jsdelivr.net/gh/LuckyZmj/imgbed@master/galleries/%E5%8A%A8%E6%BC%AB%E6%8F%92%E7%94%BB/01.jpg
- https://cdn.jsdelivr.net/gh/LuckyZmj/imgbed@master/galleries/%E5%8A%A8%E6%BC%AB%E6%8F%92%E7%94%BB/05.jpg
- https://cdn.jsdelivr.net/gh/LuckyZmj/imgbed@master/galleries/%E7%92%80%E7%92%A8%E6%98%9F%E7%A9%BA/14.jpg
- https://cdn.jsdelivr.net/gh/LuckyZmj/imgbed@master/galleries/%E7%92%80%E7%92%A8%E6%98%9F%E7%A9%BA/01.jpg
```


### 0x04 更多内容优化

以上简单介绍了 `LuckyBlog` 中一些要修改的个性化地方，其他更详细的优化参考其他关于`Matery`的文章。以下几篇文章都是基于`hexo-theme-matery`主题优化的教程，大家如果遇到问题，可以参考其中的方法。

- [个人博客搭建](http://luckyzmj.cn/posts/e3e08109.html)
- [Hexo+Github博客搭建完全教程](https://sunhwee.com/posts/6e8839eb.html)
- [hexo-theme-matery作者教程](https://github.com/blinkfox/hexo-theme-matery/blob/develop/README_CN.md)
- [Hexo+github搭建博客(超级详细版，精细入微)](https://yafine-blog.cn/posts/4ab2.html)
- [hexo（matery）背景、滚动条优化+增加点击跳评论](https://blog.csdn.net/cungudafa/article/details/106278206)
