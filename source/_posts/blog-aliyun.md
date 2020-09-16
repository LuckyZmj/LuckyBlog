---
title: 阿里云服务器部署Hexo博客
author: luckyzmj
coverImg: /medias/banner/7.jpg
top: false
cover: false
toc: true
mathjax: false
summary: 相信大部分人使用Hexo搭建个人博客都会部署到一些免费的代码托管平台上，但这些免费的平台总是差强人意，今天记录下如何在自己的云服务器上搭建Hexo博客。
tags:
  - Hexo
  - 阿里云
  - 博客
categories:
  - 博客篇
abbrlink: 19d2a4e6
reprintPolicy: cc_by
date: 2020-02-27 00:00:00
img:
password:
---

## 前言

---

&emsp;&emsp;相信大部分人使用Hexo搭建个人博客都会部署到一些免费的代码托管平台上，但这些免费的平台总是差强人意，比如国外的GitHub平台虽然完全免费，但在国内访问加载速度非常慢，又或者是国内的码云平台免费版有许多功能被阉割掉了，比如不能自定义域名，不能每次自动刷新提交的代码，需要到码云平台上手动刷新，如此一来非常繁琐。

&emsp;&emsp;为了有效解决上诉的一些问题，有条件的话，不妨在自己的云服务器上搭建Hexo博客。

## 效果演示

---

这是Hexo博客部署到GitHub上的网站测速效果

![演示demo1](https://s1.ax1x.com/2020/03/12/8mhkv9.png)

这是Hexo博客部署到阿里云服务器后的网站测速效果

![演示demo2](https://s1.ax1x.com/2020/03/12/8mWYQA.png)

## 环境准备

---

- 本地环境：Windows 10 
- 云服务器环境：阿里云ECS（CentOS7.x）

## 开始部署

---

### 本地环境搭建

**1.安装Git**

到git官网上下载.exe文件,Download git,安装选项还是全部默认，最后一步添加路径时选择`Use Git from the Windows Command Prompt`。
- Git[下载地址](https://git-scm.com/download)
- Git[教程](https://www.liaoxuefeng.com/wiki/896043488029600)


**2.安装Nodejs**

到[Node.js官网](http://nodejs.cn/download/)下载`.exe`文件，安装选项全部默认。安装好之后，按`Win+R`打开cmd命令提示符，输入`node -v`和`npm -v`，若出现版本号，则说明安装成功。

使用npm阿里的国内镜像进行加速下载

```bash
npm config set registry https://registry.npm.taobao.org
```

**4.安装Hexo**

先创建一个文件夹`MyBlog`，用来存放自己的博客文件，然后`cd`到这个文件夹下（或者在这个文件夹下直接右键`git bash here`打开）。

定位到该目录下，输入`npm install -g hexo-cli`安装`Hexo`。可能会有几个报错，不用理会。

```bash
npm install -g hexo-cli
```

安装完后输入`hexo -v`,若出现版本号则，说明安装成功。


接下来初始化一下`hexo`,即初始化我们的博客，输入`hexo init`初始化文件夹

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

输入`hexo g`生成静态网页，然后输入`hexo s`打开本地服务器预览

```bash
hexo g
hexo s
```

![Hexo](https://s1.ax1x.com/2020/03/12/8VdlGD.png)

### 生成ssh公钥

在本地桌面点击右键`Git Bash Here`打开Git终端，执行如下命令`,一路回车

```bash
ssh-keygen -t rsa
```

这个时候它会告诉你已经生成了`.ssh`的文件夹。在`git bash`中输入

```bash
cat ~/.ssh/id_rsa.pub
```

输出的内容就是公钥信息了

### 阿里云服务器环境搭建

安装`Git`

```bash
yum install git
```

创建`Git`账户

```bash
adduser git
```

添加账户权限

```bash
chmod 740 /etc/sudoers
vim /etc/sudoers
```

找到

```bash
## Allow root to run any commands anywhere
root    ALL=(ALL)     ALL
```

添加以下内容

```bash
git   ALL=(ALL)     ALL
```

保存退出并改回权限

```bash
chmod 400 /etc/sudoers
```

设置`git`账户密码

```bash
sudo passwd git
```

切换至`git`用户，创建 `~/.ssh` 文件夹和 `~/.ssh/authorized_keys` 文件，并赋予相应的权限

```bash
su git
mkdir ~/.ssh
vim ~/.ssh/authorized_keys
# 然后将win10中生成的id_rsa.pub文件中的公钥复制到authorized_keys
chmod 600 /home/git/.ssh/authorized_keys
chmod 700 /home/git/.ssh
```

在本地`Git`终端中测试是否能免密登录`git`，其中`SERVER`为填写自己的云主机`IP`，执行输入`yes`后不用密码就说明好了

```bash
ssh -v git@SERVER
```

创建目录

```bash
#repo作为为Git仓库目录
mkdir /var/repo
chown -R git:git /var/repo
chmod -R 755 /var/repo
#hexo作为网站根目录
mkdir /var/www/hexo
chown -R git:git /var/www/hexo
chmod -R 755 /var/www/hexo
```

然后创建一个裸的 `Git` 仓库

```bash
cd var/repo
git init --bare hexoBlog.git
```


创建一个新的 `Git` 钩子，用于自动部署 在 `/var/repo/hexoBlog.git` 下，有一个自动生成的 `hooks` 文件夹。我们需要在里边新建一个新的钩子文件 `post-receive`。

```bash
vim /var/repo/hexoBlog.git/hooks/post-receive
```


按 `i` 键进入文件的编辑模式，在该文件中添加两行代码（将下边的代码粘贴进去)，指定 `Git` 的工作树（源代码）和 `Git` 目录（配置文件等）

```bash
#!/bin/bash
git --work-tree=/var/www/hexo --git-dir=/var/repo/hexoBlog.git checkout -f
```

然后，按 `Esc` 键退出编辑模式，输入”`:wq`” 保存退出。

修改文件权限，使得其可执行

```bash
chown -R git:git /var/repo/hexoBlog.git/hooks/post-receive
chmod +x /var/repo/hexoBlog.git/hooks/post-receive
```

到此为止 `Git` 仓库就搭建完成了。

### 阿里云服务器配置Nginx

用宝塔面板来一键部署Nginx `Linux`面板6.0安装命令(暂时仅兼容`Centos7.x`，其它系统版本请安装5.9稳定版)：

```bash
yum install -y wget && wget -O install.sh http://download.bt.cn/install/install_6.0.sh && bash install.sh
```


`Linux`面板6.0升级专业版

```bash
curl http://download.bt.cn/install/update6.sh|bash
```

安装完成后会显示面板后台地址·账号·密码。打开面板后台地址登陆面板，选择`Nginx`的部署方案，静静等待部署。

部署完成，点击网站-添加站点-输入域名(没有域名的输入自己的`IP`地址)-底部的`PHP`版本选择”纯静态”-提交。 

网站创建完成后点击设置-配置文件

```bash
server
{
    listen 80;
  # server_name 填写自己的域名
    server_name luckyzmj.cn blog.luckyzmj.cn;
    index index.php index.html index.htm default.php default.htm default.html;
  # 这里root填写自己的网站根目录，修改为/var/www/hexo
    root /var/www/hexo;
```

-保存

点击设置-网站目录，修改为`/var/www/hexo` ，保存

重启宝塔面板服务

```bash
service bt restart
```

### 本地Hexo部署到阿里云服务器

进入到本地`Hexo`博客的文件夹`MyBlog`,右键点击`Git Bash Here`，输入命令

```bash
#定义邮箱(更换为你的邮箱地址就行)
git config --global user.email "you@example.com"
#定义名称(更换自定义一个名称就行)
git config --global user.name "Your Name"
```

配置`_config.yml`,完成自动化部署 

打开本地`Hexo`博客的文件夹`MyBlog`文件夹下的`_config.yml`, 找到`deploy`

```bash
deploy:
  type: git
  #server改为你的服务IP地址或解析后的域名
  #例如我改为repo: git@luckyzmj.cn:/var/repo/blog.git
  repo: git@server:/var/repo/blog.git
  branch: master
```

保存后，即可测试部署

再进入到本地`Hexo`博客的文件夹`MyBlog`,右键点击`Git Bash Here`，输入命令

```bash
hexo clean 
hexo g -d
```

不报错说明完成，打开浏览器输入你的域名或`ip`地址就可以看到你部署的`Hexo`博客了。 

到此为止，我们已经成功部完成，并且访问自己的服务器端比访问Github快多了。

>### 小贴士

在部署过程中，执行 hexo d发现部署老是出错，什么权限不允许之类的，这里我们需要检查我们在上述的`git`操作部署是否使用了`git`用户操作，若是没有，需要给相应的目录更改用户组 使用

```bash
chown -R git:git /var/repo/
```

这条命令递归的将`repo`目录及其子目录用户组设置为`git`。 同时使用

```bash
chown -R git:git /var/www/hexo
```
这样即可解决此类问题。

还有一个问题就是绑定域名后不能访问。原因是在国内任何域名只要绑定到国内的服务器主机上都必须去工信部和公安部备案完后才能正常使用。如果是港澳台的服务器或者是国外的服务器则可以不需要备案。

## 参考文章

- https://blog.csdn.net/weixin_33907511/article/details/91398208?utm_source=distribute.pc_relevant.none-task