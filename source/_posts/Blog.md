---
title: 个人博客搭建
author: luckyzmj
coverImg: /medias/banner/7.jpg
top: false
cover: true
toc: true
mathjax: false
summary: >-
  前前后后大概花了2周的时间，目前个人博客已经完善的差不多了，现在写个文章做个阶段总结，后续如果有更新的地方，会及时补充。本博客基于Hexo框架，采用hexo-theme-matery主题，并在此基础上做了改进。
tags:
  - Hexo
  - Github
  - 博客
categories:
  - 博客篇
abbrlink: e3e08109
date: 2019-08-27 11:41:03
img:
password:
reprintPolicy: cc_by
---

## 0x001 效果演示

---

![演示Demo](https://s2.ax1x.com/2020/03/11/8E3bBF.png)

## 0x002 简单介绍

---

&emsp;&emsp;前前后后大概花了一周多的时间，目前个人博客已经完善的差不多了，现在写个文章做个阶段总结，后续如果有更新的地方，会及时补充。本博客基于Hexo框架，采用[hexo-theme-matery](https://github.com/blinkfox/hexo-theme-matery/blob/develop/README_CN.md)主题，在这里非常感谢作者`洪卫`的[hexo-blog-fly](https://github.com/shw2018/hexo-blog-fly.git)博客开源，极大简化了构建博客的工作量和复杂度。在此开源博客的基础上做了改进，修复了一些bug，顺利搭建完成了我的个人博客。大家对此主题有兴趣的可以[下载源代码](https://github.com/shw2018/hexo-blog-fly)，搭建属于自己的个性化博客。
- 个人博客 演示：[http://luckyzmj.cn](http://luckyzmj.cn)

---

## 0x003 Hexo 初级搭建

---

### 1. 安装Git
`Git`是目前世界上最先进的分布式版本控制系统，可以有效、高速的处理从很小到非常大的项目版本管理。`Git`的作用是将本地的网页文件传到`github`上。

- Git[下载地址](https://git-scm.com/download)
- Git[教程](https://www.liaoxuefeng.com/wiki/896043488029600)

**windows：** 到git官网上下载.exe文件,Download git,安装选项还是全部默认，最后一步添加路径时选择`Use Git from the Windows Command Prompt`。

### 2. 安装node.js
`Hexo`是基于`node.js`编写的，所以需要安装一下`node.js`和里面的`npm`工具。

**windows：** 到[Node.js官网](http://nodejs.cn/download/)下载`.exe`文件，安装选项全部默认。安装好之后，按`Win+R`打开cmd命令提示符，输入`node -v`和`npm -v`，若出现版本号，则说明安装成功。

### 3. 添加npm国内源

使用阿里的国内镜像进行加速下载

```bash
npm config set registry https://registry.npm.taobao.org
```

### 4. 安装Hexo

前面`git`和`nodejs`安装好后，就可以安装`hexo`了，你可以先创建一个文件夹`MyBlog`，用来存放自己的博客文件，然后`cd`到这个文件夹下（或者在这个文件夹下直接右键`git bash`打开）。

比如我的博客文件都存放在`E:\MyBlog`目录下。

在该目录下右键点击`Git Bash Here`，打开`git`的控制台窗口，以后我们所有的操作都在`git`控制台进行，就不用`Windows`自带的`cmd`了。

定位到该目录下，输入`npm install -g hexo-cli`安装`Hexo`。可能会有几个报错，不用理会。

```bash
npm install -g hexo-cli
```

安装完后输入`hexo -v`验证是否安装成功。

到此为止`hexo`就安装完了。

接下来初始化一下`hexo`,即初始化我们的网站，输入`hexo init`初始化文件夹

```bash
hexo init MyBlog
```

新建完成后，指定文件夹`MyBlog`目录下有：

- `node_modules`: 依赖包
- `public`：存放生成的页面
- `scaffolds`：生成文章的一些模板
- `source`：用来存放你的文章
- `themes`：主题**
- `_config.yml`: 博客的配置文件**

到此为止，本地的网站配置完成了。

输入`hexo g`生成静态网页，然后输入`hexo s`打开本地服务器

```bash
hexo g
hexo s
```

![](https://s1.ax1x.com/2020/03/12/8VdlGD.png)

### 5. 注册Github账号创建个人仓库

接下来就去注册一个`github`账号，用来存放我们的网站。

打开[https://github.com/](https://github.com/)，新建一个项目仓库`New repository`，如下所示：

![](https://s1.ax1x.com/2020/03/12/8VwrtK.png)

然后如下图所示，输入自己的项目名字，后面一定要加`.github.io`后缀，README初始化也要勾上

![](https://s1.ax1x.com/2020/03/12/8VdoQJ.png)

>要创建一个和你用户名相同的仓库，后面加`.github.io`，只有这样，将来要部署到`GitHub page`的时候，才会被识别，也就是`http://xxxx.github.io`，其中xxx就是你注册`GitHub`的用户名。例如我的：`http://LuckyZmj.github.io`

### 6. 生成SSH添加到GitHub

生成`SSH`添加到`GitHub`，连接`Github`与本地。
右键打开`git bash here`，然后输入下面命令：

```bash
git config --global user.name "注册GitHub用户名"
git config --global user.email "注册GitHub的邮箱"
```

用以下两条，检查一下你有没有输对

```bash
git config user.name
git config user.email
```

然后创建`SSH`,一路回车

```bash
ssh-keygen -t rsa -C "注册GitHub的邮箱"
```

这个时候它会告诉你已经生成了`.ssh`的文件夹。在`git bash`中输入

```bash
cat ~/.ssh/id_rsa.pub
```

将输出的内容复制到框中，点击确定保存。

打开`github`，在头像下面点击`settings`，再点击`SSH and GPG keys`，新建一个`SSH`，名字随便取一个都可以，把你的`id_rsa.pub`里面的信息复制进去。如图：

![](https://s1.ax1x.com/2020/03/12/8Vwnyj.png)

在`git bash`输入`ssh -T git@github.com`，如果如下图所示，出现你的用户名，那就成功了。

```bash
ssh -T git@github.com
```

### 7. 将hexo部署到GitHub
将`hexo`生成的文章部署到`GitHub`上，打开博客根目录下的`_config.yml`文件，这是博客的配置文件，在这里你可以修改与博客配置相关的各种信息。
找到如下配置进行修改：

```bash
deploy:
  type: git
  repository: https://github.com/LuckyZmj/LuckyZmj.github.io
  branch: master
```

`repository`修改为你自己的`github`项目地址即可，就是部署时，告诉工具，将生成网页通过`git`方式上传到你对应的链接仓库中。

这个时候需要先安装`deploy-git` ，也就是部署的命令,这样你才能用命令部署到`GitHub`。

```bash
npm install hexo-deployer-git --save
```

然后就可以部署提交到`github`，过一会儿就可以在`http://yourname.github.io` 这个网站看到你的博客了

```bash
hexo clean
hexo generate
hexo deploy
```
其中 `hexo clean`清除了你之前生成的东西。 `hexo generate`，生成静态文章，可以用 `hexo g`缩写 ，`hexo deploy`部署文章，可以用`hexo d`缩写

>注意`deploy`时可能要你输入`username`和`password`。

### 8. 写文章和发布文章

首先在博客根目录下右键打开`git bash here`，安装一个扩展`npm i hexo-deployer-git`。

```bash
npm i hexo-deployer-git
```

然后输入`hexo new post "article title"`，新建一篇文章。

```bash
hexo new post "article title"
```

然后打开`E:\MyBlog\source\_posts`的目录，可以发现下面多了一个文件夹和一个`.md`文件，一个用来存放你的图片等数据，另一个就是你的文章文件。

另外推荐直接使用`有道云`编写`markdown`文章，不仅可以实时预览，还可以快捷的生成`markdown`语法格式，具体效果如下图所示。

![有道云](https://s1.ax1x.com/2020/03/12/8VwItf.png)

编写完`markdown`文件后，根目录下输入`hexo g`生成静态网页，然后输入`hexo s`可以本地预览效果，最后输入`hexo d`上传到`github`上。这时打开你的`github.io`主页就能看到发布的文章了。

到此为止，`Hexo`初级搭建就已经完成了。

## 0x004 Hexo 优化定制

---

### 1. Hexo相关目录文件

#### 1.1 博客目录构成介绍

`node_modules`是`node.js`各种库的目录，`public`是生成的网页文件目录，`scaffolds`里面就三个文件，存储着新文章和新页面的初始设置，`source`是我们最常用到的一个目录，里面存放着文章、各类页面、图像等文件，`themes`存放着主题文件，一般也用不到。

我们平时写文章只需要关注`source/_posts`这个文件夹就行了。

```bash
- node_modules
- public
- scaffolds
- source
    - _data
    - _posts
    - about
    - archives
    - categories
    - friends
    - tags
- themes
```

#### 1.2 hexo基本配置

在文件根目录下的`_config.yml`，就是整`个hexo`框架的配置文件了。可以在里面修改大部分的配置。详细可参考官方的[配置描述](https://hexo.io/zh-cn/docs/configuration)。

##### 1.2.1 网站

参数描述`title`网站标题`subtitle`网站副标题`description`网站描述`author`您的名字`language`网站使用的语言`timezone`网站时区。`Hexo` 默认使用您电脑的时区。时区列表。比如说：`America/New_York`, `Japan`, 和 `UTC` 。

其中，`description`主要用于`SEO`，告诉搜索引擎一个关于您站点的简单描述，通常建议在其中包含您网站的关键词。`author`参数用于主题显示文章的作者。

##### 1.2.2 网址

参数描述`url`网址`root`网站根目录 `permalink`文章的[永久链接](https://hexo.io/zh-cn/docs/permalinks)格式`permalink_defaults`永久链接中各部分的默认值

在这里，你需要把`url`改成你的网站域名。

`permalink`，也就是你生成某个文章时的那个链接格式。

比如我新建一个文章叫`temp.md`，那么这个时候他自动生成的地址就是`http://yoursite.com/2018/09/05/temp`。

以下是官方给出的示例，关于链接的变量还有很多，需要的可以去官网上查找[永久链接](https://hexo.io/zh-cn/docs/permalinks) 。

```bash
参数结果
:year/:month/:day/:title       /2019/08/10/hello-world 
:year-:month-:day-:title.html  2019-08-10-hello-world.html 
:category/:titlefoo            /bar/hello-world
```

### 2. 定制主题

这里推荐作者`洪卫`的[hexo-blog-fly](https://github.com/shw2018/hexo-blog-fly.git)博客主题，该主题是基于[hexo-theme-matery](https://github.com/blinkfox/hexo-theme-matery)优化的，需要把博客相关信息换成您自己的就可以部署了，极大简化了构建博客的工作量和复杂度。

#### 2.1 简单使用方法 
1. 安装`Git`, 安装`nodeJS`，安装`Hexo`
1. 你可以直接`fork`一份源码到你的仓库，`clone`到本地博客文件夹内
1. 在本地博客仓库运行`npm i`命令安装依赖包
1. 直接修改配置信息，改成自己的信息
1. 运行命令`hexo clean`（清除生成文件），`hexo g`（生成网页）， `hexo s`（本地预览），`hexo d`（部署）

#### 2.2 原主题特性:

- 简单漂亮，文章内容美观易读
- [Material Design](https://material.io/) 设计
- 响应式设计，博客在桌面端、平板、手机等设备上均能很好的展现
- 首页轮播文章及每天动态切换 `Banner` 图片
- 瀑布流式的博客文章列表（文章无特色图片时会有 `24` 张漂亮的图片代替）
- 时间轴式的归档页
- **词云**的标签页和**雷达图**的分类页
- 丰富的关于我页面（包括关于我、文章统计图、我的项目、我的技能、相册等）
- 可自定义的数据的友情链接页面
- 支持文章置顶和文章打赏
- 支持 `MathJax`
- `TOC` 目录
- 可设置复制文章内容时追加版权信息
- 可设置阅读文章时做密码验证
- [Gitalk](https://gitalk.github.io/)、[Gitment](https://imsun.github.io/gitment/)、[Valine](https://valine.js.org/) 和 [Disqus](https://disqus.com/) 评论模块（推荐使用 `Gitalk`）
- 集成了[不蒜子统计](http://busuanzi.ibruce.info/)、谷歌分析（`Google Analytics`）和文章字数统计等功能
- 支持在首页的音乐播放和视频播放功能

#### 2.3 新增加特性:
- 修改了原主题的一些很多bug
- 加入图片懒加载功能，在根目录配置文件开启和关闭
- 增加留言板功能
- 在关于板块,加入简历功能页
- 增加视听[视觉听觉影音]板块 
- 支持emoji表情，用markdown emoji语法书写直接生成对应的能跳跃的表情。
- 增加网站运行时间显示 
- 增加动漫模型 
- 整体替换Banner图片和文章特色图片
- 增加分类相册功能
- 修改了一些控件的参数
- 修改部分样式,比如: 文章卡片,固定高度,使其不至于因为文章摘要的长短不同导致卡片大小不一使页面布局很不美观,类似的还有友链卡片,优化了页面内容布局,视觉更整齐美观
- 解决首页文章列表卡片上方 border-radius圆角失效的bug
- 添加页面樱花飘落动效
- 添加鼠标点击烟花爆炸动效
- 加入天气接口控件
- 加入鼠标点击文字特效
- 添加页面雪花飘落动效
- 添加在线聊天插件
- 调整线聊天插件参数，使之能够随着鼠标滑动位置自适应调整
- 持续更新...
---

#### 2.4 切换主题

如果想自己动手对[hexo-theme-matery](https://github.com/blinkfox/hexo-theme-matery)优化的话，可以修改Hexo根目录下的` _config.yml`的 `theme` 的值

```bash
theme: hexo-theme-matery
```

`_config.yml` 文件的其它修改建议:

- 请修改 `_config.yml` 的 `url` 的值为你的网站主 `URL`（如：`http://xxx.github.io`）。
- 建议修改两个 `per_page` 的分页条数值为 6 的倍数，如：12、18 等，这样文章列表在各个屏幕下都能较好的显示。
- 如果你是中文用户，则建议修改 `language` 的值为 `zh-CN`。

#### 2.5 新建分类 categories 页

`categories` 页是用来展示所有分类的页面，如果在你的博客 `source` 目录下还没有 `categories/index.md` 文件，那么你就需要新建一个，命令如下：

```bash
hexo new page "categories"
```

编辑你刚刚新建的页面文件 `/source/categories/index.md`，至少需要以下内容：

```bash
---
title: categories
date: 2018-09-30 17:25:30
type: "categories"
layout: "categories"
---
```

#### 2.6 新建标签 tags 页

`tags` 页是用来展示所有标签的页面，如果在你的博客 `source` 目录下还没有 `tags/index.md` 文件，那么你就需要新建一个，命令如下：

```bash
hexo new page "tags"
```

编辑你刚刚新建的页面文件 `/source/tags/index.md`，至少需要以下内容：

```bash
---
title: tags
date: 2018-09-30 18:23:38
type: "tags"
layout: "tags"
---
```

#### 2.7 新建关于我 about 页

`about` 页是用来展示关于我和我的博客信息的页面，如果在你的博客 `source` 目录下还没有 `about/index.md` 文件，那么你就需要新建一个，命令如下：

```bash
hexo new page "about"
```

编辑你刚刚新建的页面文件 `/source/about/index.md`，至少需要以下内容：

```bash
---
title: about
date: 2018-09-30 17:25:30
type: "about"
layout: "about"
---
```

#### 2.8 新建留言板 contact 页（可选的）

`contact` 页是用来展示留言板信息的页面，前提是已经开启了第三方评论系统才能显示。如果在你的博客 `source` 目录下还没有 `contact/index.md` 文件，那么你就需要新建一个，命令如下：

```bash
hexo new page "contact"
```

编辑你刚刚新建的页面文件 `/source/contact/index.md`，至少需要以下内容：

```bash
---
title: contact
date: 2018-09-30 17:25:30
type: "contact"
layout: "contact"
---
```

#### 2.9 新建友情链接 friends 页（可选的）

`friends` 页是用来展示友情链接信息的页面，如果在你的博客 `source` 目录下还没有 `friends/index.md` 文件，那么你就需要新建一个，命令如下：

```bash
hexo new page "friends"
```

编辑你刚刚新建的页面文件 `/source/friends/index.md`，至少需要以下内容：

```bash
---
title: friends
date: 2018-12-12 21:25:30
type: "friends"
layout: "friends"
---
```

同时，在你的博客 `source` 目录下新建 `_data` 目录，在 `_data` 目录中新建 `friends.json` 文件，文件内容如下所示：

```bash
[{
    "avatar": "http://image.luokangyuan.com/1_qq_27922023.jpg",
    "name": "码酱",
    "introduction": "我不是大佬，只是在追寻大佬的脚步",
    "url": "http://luokangyuan.com/",
    "title": "前去学习"
}, {
    "avatar": "http://image.luokangyuan.com/4027734.jpeg",
    "name": "闪烁之狐",
    "introduction": "编程界大佬，技术牛，人还特别好，不懂的都可以请教大佬",
    "url": "https://blinkfox.github.io/",
    "title": "前去学习"
}, {
    "avatar": "http://image.luokangyuan.com/avatar.jpg",
    "name": "ja_rome",
    "introduction": "平凡的脚步也可以走出伟大的行程",
    "url": "https://me.csdn.net/jlh912008548",
    "title": "前去学习"
}]
```

#### 2.10 一级菜单导航配置
配置基本菜单导航的名称、路径`url`和图标`icon`

- 菜单导航名称可以是中文也可以是英文(如：`Index`或主页) 
- 图标`icon` 可以在`Font Awesome` 中查找

```bash
menu:
  Index:
    url: /
    icon: fas fa-home
  Tags:
    url: /tags
    icon: fas fa-tags
  Categories:
    url: /categories
    icon: fas fa-bookmark
  Archives:
    url: /archives
    icon: fas fa-archive
  About:
    url: /about
    icon: fas fa-user-circle
  Friends:
    url: /friends
    icon: fas fa-address-book
```

#### 2.11 二级菜单配置方法

如果你需要二级菜单则可以在原基本菜单导航的基础上如下操作
- 在需要添加二级菜单的一级菜单下添加`children`关键字(如:`About`菜单下添加`children`)
- 在`children`下创建二级菜单的 名称`name`,路径`url`和图标`icon`.
- 注意每个二级菜单模块前要加 -.
- 注意缩进格式

```bash
menu:
  Index:
    url: /
    icon: fas fa-home
  Tags:
    url: /tags
    icon: fas fa-tags
  Categories:
    url: /categories
    icon: fas fa-bookmark
  Archives:
    url: /archives
    icon: fas fa-archive
  About:
    url: /about
    icon: fas fa-user-circle-o
  Friends:
    url: /friends
    icon: fas fa-address-book
  Medias:
    icon: fas fa-list
    children:
      - name: Musics
        url: /musics
        icon: fas fa-music
      - name: Movies
        url: /movies
        icon: fas fa-film
      - name: Books
        url: /books
        icon: fas fa-book
      - name: Galleries
        url: /galleries
        icon: fas fa-image
```

执行 `hexo clean` && `hexo g` 重新生成博客文件。

#### 2.12 代码高亮

由于 `Hexo` 自带的代码高亮主题显示不好看，所以主题中使用到了 `hexo-prism-plugin` 的 `Hexo` 插件来做代码高亮，安装命令如下：

```bash
npm i -S hexo-prism-plugin
```

然后，修改 `Hexo` 根目录下 `_config.yml` 文件中 `highlight.enable` 的值为 `false`，并新增 `prism` 插件相关的配置，主要配置如下：

```bash
highlight:
  enable: false

prism_plugin:
  mode: 'preprocess'    # realtime/preprocess
  theme: 'tomorrow'
  line_number: false    # default false
  custom_css:
```

>更多代码块优化详细内容请访问：http://luckyzmj.cn/posts/1b9a9e28.html

#### 2.13 搜索

本主题中还使用到了 `hexo-generator-search` 的 `Hexo` 插件来做内容搜索，安装命令如下：

```bash
npm install hexo-generator-search --save
```

在 `Hexo` 根目录下的 `_config.yml` 文件中，新增以下的配置项：

```bash
search:
  path: search.xml
  field: post
```

#### 2.14 文章字数统计插件（建议安装）

如果你想要在文章中显示文章字数、阅读时长信息，可以安装 `hexo-wordcount` 插件。

安装命令如下：

```bash
npm i --save hexo-wordcount
```

然后只需在本主题下的 `_config.yml` 文件中，将各个文章字数相关的配置激活即可：

```bash
postInfo:
  date: true
  update: false
  wordCount: false # 设置文章字数统计为 true.
  totalCount: false # 设置站点文章总字数统计为 true.
  min2read: false # 阅读时长.
  readCount: false # 阅读次数.
```

#### 2.15 添加emoji表情支持（可选的）

本主题新增了对`emoji`表情的支持，使用到了 `hexo-filter-github-emojis` 的 `Hexo` 插件来支持 `emoji`表情的生成，把对应的`markdown` `emoji`语法（::,例如：`:smile:`）转变成会跳跃的`emoji`表情，安装命令如下：

```bash
npm install hexo-filter-github-emojis --save
```

在 `Hexo` 根目录下的 `_config.yml` 文件中，新增以下的配置项：

```bash
githubEmojis:
  enable: true
  className: github-emoji
  inject: true
  styles:
  customEmojis:
```

#### 2.16 添加 RSS 订阅支持（可选的）

本主题中还使用到了`hexo-generator-feed`  的 `Hexo` 插件来做 `RSS`，安装命令如下：

```bash
npm install hexo-generator-feed --save
```

在 `Hexo` 根目录下的` _config.yml` 文件中，新增以下的配置项：

```bash
feed:
  type: atom
  path: atom.xml
  limit: 20
  hub:
  content:
  content_limit: 140
  content_limit_delim: ' '
  order_by: -date
```

执行 `hexo clean` && `hexo g` 重新生成博客文件，然后在 `public` 文件夹中即可看到 `atom.xml` 文件，说明你已经安装成功了。

#### 2.17 添加 DaoVoice 在线聊天功能（可选的）

前往 `DaoVoice` 官网注册并且获取 `app_id`，并将 `app_id` 填入主题的 `_config.yml` 文件中。

#### 2.18 添加 Tidio 在线聊天功能（可选的）

前往 `Tidio` 官网注册并且获取 `Public Key`，并将 `Public Key` 填入主题的 `_config.yml` 文件中。

#### 2.19 修改页脚

页脚信息可能需要做定制化修改，而且它不便于做成配置信息，所以可能需要你自己去再修改和加工。修改的地方在主题文件的 `/layout/_partial/footer.ejs` 文件中，包括站点、使用的主题、访问量等。

#### 2.20 修改社交链接

在主题的 `_config.yml` 文件中，默认支持 `QQ`、`GitHub` 和邮箱等的配置，你可以在主题文件的 `/layout/_partial/social-link.ejs` 文件中，新增、修改你需要的社交链接地址，增加链接可参考如下代码：

```html
<% if (theme.socialLink.github) { %>
    <a href="<%= theme.socialLink.github %>" class="tooltipped" target="_blank" data-tooltip="访问我的GitHub" data-position="top" data-delay="50">
        <i class="fab fa-github"></i>
    </a>
<% } %>
```

其中，社交图标（如：`fa-github`）你可以在 `Font Awesome` 中搜索找到。以下是常用社交图标的标识，供你参考：

- Facebook: fab fa-facebook
- Twitter: fab fa-twitter
- Google-plus: fab fa-google-plus
- Linkedin: fab fa-linkedin
- Tumblr: fab fa-tumblr
- Medium: fab fa-medium
- Slack: fab fa-slack
- Sina Weibo: fab fa-weibo
- Wechat: fab fa-weixin
- QQ: fab fa-qq
- Zhihu: fab fa-zhihu

注意: 本主题中使用的 `Font Awesome` 版本为 5.11.0。

#### 2.21 修改打赏的二维码图片

在主题文件的 `source/medias/reward` 文件中，你可以替换成你的的微信和支付宝的打赏二维码图片。

#### 2.22 配置音乐播放器（可选的）

要支持音乐播放，在主题的 `_config.yml` 配置文件中激活`music`配置即可


```bash
# 是否在首页显示音乐
music:
  enable: true
  title:     	    #非吸底模式有效
    enable: true
    show: 听听音乐
  server: netease   #require music platform: netease, tencent, kugou, xiami, baidu
  type: playlist    #require song, playlist, album, search, artist
  id: 503838841     #require song id / playlist id / album id / search keyword
  fixed: false      # 开启吸底模式
  autoplay: false   # 是否自动播放
  theme: '#42b983'
  loop: 'all'       # 音频循环播放, 可选值: 'all', 'one', 'none'
  order: 'random'   # 音频循环顺序, 可选值: 'list', 'random'
  preload: 'auto'   # 预加载，可选值: 'none', 'metadata', 'auto'
  volume: 0.7       # 默认音量，请注意播放器会记忆用户设置，用户手动设置音量后默认音量即失效
  listFolded: true  # 列表默认折叠

提示：
    server可选netease（网易云音乐），tencent（QQ音乐），kugou（酷狗音乐），xiami（虾米音乐），baidu（百度音乐）。

    type可选song（歌曲），playlist（歌单），album（专辑），search（搜索关键字），artist（歌手）

    id获取示例: 浏览器打开网易云音乐，点击我喜欢的音乐歌单，地址栏有一串数字，playlist的id即为这串数字。
```

#### 2.23文章 Front-matter 介绍

`Front-matter` 选项中的所有内容均为非必填的。但我仍然建议至少填写 `title` 和 `date` 的值。

配置选项 | 默认值 |	描述
---|---|---
title |	Markdown 的文件标题 | 文章标题，强烈建议填写此选项
date | 文件创建时的日期时间 |	发布时间，强烈建议填写此选项，且最好保证全局唯一
author | 根 _config.yml 中的 author | 文章作者
img | featureImages 中的某个值 |	文章特征图，推荐使用图床(腾讯云、七牛云、又拍云等)来做图片的路径.如: http://xxx.com/xxx.jpg
top | true | 推荐文章（文章是否置顶），如果 top 值为 true，则会作为首页推荐文章
cover | false | v1.0.2版本新增，表示该文章是否需要加入到首页轮播封面中
coverImg | 无 | v1.0.2版本新增，表示该文章在首页轮播封面需要显示的图片路径，如果没有，则默认使用文章的特色图片
password | 无 | 文章阅读密码，如果要对文章设置阅读验证密码的话，就可以设置 password 的值，该值必须是用 SHA256 加密后的密码，防止被他人识破。前提是在主题的 config.yml 中激活了 verifyPassword 选项
toc | true | 是否开启 TOC，可以针对某篇文章单独关闭 TOC 的功能。前提是在主题的 config.yml 中激活了 toc 选项
mathjax | false | 是否开启数学公式支持 ，本文章是否开启 mathjax，且需要在主题的 _config.yml 文件中也需要开启才行
summary | 无 | 文章摘要，自定义的文章摘要内容，如果这个属性有值，文章卡片摘要就显示这段文字，否则程序会自动截取文章的部分内容作为摘要
categories | 无 | 文章分类，本主题的分类表示宏观上大的分类，只建议一篇文章一个分类
tags | 无 | 文章标签，一篇文章可以多个标签
keywords | 文章标题 | 文章关键字，SEO 时需要
reprintPolicy | cc_by | 文章转载规则， 可以是 cc_by, cc_by_nd, cc_by_sa, cc_by_nc, cc_by_nc_nd, cc_by_nc_sa, cc0, noreprint 或 pay 中的一个


```bash
注意:
    如果 img 属性不填写的话，文章特色图会根据文章标题的 hashcode 的值取余，然后选取主题中对应的特色图片，从而达到让所有文章都的特色图各有特色。
    date 的值尽量保证每篇文章是唯一的，因为本主题中 Gitalk 和 Gitment 识别 id 是通过 date 的值来作为唯一标识的。
    如果要对文章设置阅读验证密码的功能，不仅要在 Front-matter 中设置采用了 SHA256 加密的 password 的值，还需要在主题的 _config.yml 中激活了配置。有些在线的 SHA256 加密的地址，可供你使用：开源中国在线工具、chahuo、站长工具。
    您可以在文章md文件的 front-matter 中指定 reprintPolicy 来给单个文章配置转载规则
```


以下为文章的 `Front-matter` 示例。
最简示例

```bash
---
title: typora-vue-theme主题介绍
date: 2018-09-07 09:25:00
---
```

最全示例

```bash
---
title: theme主题介绍
date: 2018-09-07 09:25:00
author: 赵奇
img: /source/images/xxx.jpg
top: true
cover: true
coverImg: /images/1.jpg
password: 8d969eef6ecad3c29a3a629280e686cf0c3f5d5a86aff3ca12020c923adc6c92
toc: false
mathjax: false
summary: 这是你自定义的文章摘要内容，如果这个属性有值，文章卡片摘要就显示这段文字，否则程序会自动截取文章的部分内容作为摘要
categories: Markdown
tags:
  - Typora
  - Markdown
---
```

#### 2.24 自定制修改

在本主题的 `_config.yml` 中可以修改部分自定义信息，有以下几个部分：

- 菜单
- 我的梦想
- 首页的音乐播放器和视频播放器配置
- 是否显示推荐文章名称和按钮配置
- favicon 和 Logo
- 个人信息
- TOC 目录
- 文章打赏信息
- 复制文章内容时追加版权信息
- MathJax
- 文章字数统计、阅读时长
- 点击页面的'爱心'效果
- 我的项目
- 我的技能
- 我的相册
- Gitalk、Gitment、Valine 和 disqus 评论配置
- 不蒜子统计和谷歌分析（Google Analytics）
- 默认特色图的集合。当文章没有设置特色图时，本主题会根据文章标题的 hashcode 值取余，来选择展示对应的特色图

我认为个人博客应该都有自己的风格和特色。如果本主题中的诸多功能和主题色彩你不满意，可以在主题中自定义修改，很多更自由的功能和细节点的修改难以在主题的 _config.yml 中完成，需要修改源代码才来完成。以下列出了可能对你有用的地方：
修改主题颜色

在主题文件的 `/source/css/matery.css` 文件中，搜索 `.bg-color` 来修改背景颜色：

```css
/* 整体背景颜色，包括导航、移动端的导航、页尾、标签页等的背景颜色. */
.bg-color {
    background-image: linear-gradient(to right, #4cbf30 0%, #0f9d58 100%);
}

@-webkit-keyframes rainbow {
   /* 动态切换背景颜色. */
}

@keyframes rainbow {
    /* 动态切换背景颜色. */
}

body {
    /* background-color: #eaeaea; */
    /* 增加背景壁纸*/
    background: url("https://ae01.alicdn.com/kf/H18a4b998752a4ae68b8e85d432a5aef0l.png"), url("http://luckyzmj.cn/img/yun.jpg") 0px 0px;
    background-attachment: fixed;
    margin: 0;
    color: #34495e;
}
```

#### 2.25 修改 banner 图和文章特色图

你可以直接在 `/source/medias/banner` 文件夹中更换你喜欢的 `banner` 图片，主题代码中是每天动态切换一张，只需 7 张即可。如果你会 `JavaScript` 代码，可以修改成你自己喜欢切换逻辑，如：随机切换等，banner 切换的代码位置在 `/layout/_partial/bg-cover-content.ejs` 文件的 `<script></script>` 代码中：

```css
$('.bg-cover').css('background-image', 'url(/medias/banner/' + new Date().getDay() + '.jpg)');
```

在 `/source/medias/featureimages` 文件夹中默认有 24 张特色图片，你可以再增加或者减少，并需要在 `_config.yml` 做同步修改。


#### 2.26 优化目录栏

在 `themes\Matery\layout\_partial\post-detail-toc.ejs`，修改内容如下：

```css
.toc-widget {
    padding-left: 20px;
    width: 345px;
    background-color: rgb(255, 255, 255,0.7);
    border-radius: 10px;
    box-shadow: 0 10px 35px 2px rgba(0, 0, 0, .15), 0 5px 15px rgba(0, 0, 0, .07), 0 2px 5px -5px rgba(0, 0, 0, .1) !important;
}

#toc-content {
    margin-bottom: 20px;
}
```


## 0x005 更多详细教程

以下几篇文章都是基于`Hexo`框架和`hexo-theme-matery`主题优化的教程，大家如果遇到问题，可以参考其中的方法。
- [Hexo+Github博客搭建完全教程](https://sunhwee.com/posts/6e8839eb.html)
- [hexo-theme-matery作者教程](https://github.com/blinkfox/hexo-theme-matery/blob/develop/README_CN.md)
- [Hexo+github搭建博客(超级详细版，精细入微)](https://yafine-blog.cn/posts/4ab2.html)
- [hexo（matery）背景、滚动条优化+增加点击跳评论](https://blog.csdn.net/cungudafa/article/details/106278206)
