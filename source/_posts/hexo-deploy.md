---
title: hexo一键部署到云服务器
date: 2018-05-01 11:44:37
tags:
  - Hexo
categories:
  - Hexo
  - Setup and deployment
---
上一篇记录了[如何搭建一个简易的个人网站](hexo-build.html)，采用`hexo`，`github pages`进行搭建与部署。
本篇主要记录下如何将hexo博客部署到非`github pages`的第三方云服务器上，并实现一键部署。

> 以下本地操作均在Ubuntu 18.04.1 LTS中进行测试。
> 以下云服务器上操作在阿里云Ubuntu 16.04.4 LTS \n \l中进行测试。

### 准备工作
- [x] 一台云服务器（阿里云、腾讯云等）
- [x] 已有hexo博客框架搭建的博客（具体可参考我[上一篇记录文章](hexo-build.html)）

## # 传统部署方法

#### 打包本地hexo博客项目，上传到云服务器上，再配置nginx。

##### 打包生成静态文件
```shell
$ hexo generate
```
##### 把根目录下生成的`public`文件夹压缩上传到云服务器根目录下
```shell
# 压缩成html.zip
$ zip -q -r html.zip public
# 将html.zip上传到云服务器
$ scp html.zip 用户名@服务器公网ip:~
```
##### 服务器上解压文件
```shell
# 先登录自己的服务器
$ ssh 用户名@服务器公网ip
# 找到刚上传上来的html.zip并解压缩，我这里把解压缩的文件放在/var/www/blog/下面
$ cd /var/www
$ sudo mkdir blog
$ cd blog
$ sudo cp ~/html.zip .
$ sudo unzip html.zip
# 得到public文件
```
##### 配置nginx
如果你服务器上已经安装了nginx，直接看下面。否则参考[nginx的安装与配置](https://yq.aliyun.com/articles/710641?spm=5176.10695662.1996646101.searchclickresult.155256a0P4F06Z&aly_as=MUa5PXuo)
启动ngxin，正常安装完成后默认已经启动
```shell
$ sudo nginx
```
浏览器访问服务器ip查看nginx是否安装并启动。
出现`Welcome to nginx!`字样说明启动成功，否则自行搜索解决问题。

现在配置hexo博客nginx
```shell
# nginx配置文件在/etc/nginx下
$ cd /etc/nginx/sites-enabled
# 文件夹下有default文件，是默认配置文件，修改它
$ sudo vim default
```
打开以后如下图显示
![](/images/hexo-deploy/nginx-default.png)
修改红框标注的地方为你之前解压html.zip的目录，即`/var/www/blog/public`。
保存退出，重载nginx。
```shell
$ sudo nginx -s reload
```
再次访问访问服务器ip，现在应该出现的是你博客主页了。

----

#### 以上是平时常见的部署方式，容易理解。但是过程复杂，每次更新博客需要重新部署，重复以上繁杂操作。

#### 接下来介绍一种一劳永逸的部署方式

----

## # 一劳永逸的一键部署方式

### 原理与思路
>- 类似于hexo博客`一键部署`功能，利用`hexo d`命令完成部署。
>- 借助git完成部署，在服务器上建立一个git仓库，通过命令把代码提交到git仓库，并且触发`git hooks`配置bash命令自动执行完成目录拷贝。说白了，就是常见的部署方式自动化执行的过程。

### 第一步，在服务器上创建仓库
```bash
$ mkdir blog.git
$ cd blog.git
$ git init --bare
```

如果提示git不存在，请先安装git，否则进行下一步。

### 第二步，设置自动部署钩子，也就是配置git hooks
进入hooks目录下，创建`post-receive`钩子文件
```bash
$ cd hooks
$ touch post-receive
```
编辑`post-receive`
```bash
$ sudo vim post-receive
```
输入以下内容，并保存退出
```
GIT_REPO=/var/www/blog.git
TMP_GIT_CLONE=/var/www/tmp/blog
PUBLIC_WWW=/var/www/blog
rm -rf ${TMP_GIT_CLONE}
git clone $GIT_REPO $TMP_GIT_CLONE
rm -rf ${PUBLIC_WWW}/*
cp -rf ${TMP_GIT_CLONE}/ ${PUBLIC_WWW}
```

配置解释：
>- `GIT_REPO`： 服务器git仓库所在目录，此目录并不放博客项目。
- `TMP_GIT_CLONE`： 临时目录，git会将提交的文件先存到临时目录。
- `PUBLIC_WWW`： 服务器上放博客项目的目录，你想将博客放在哪，修改此项即可。 注意此目录应对于`nginx root`设置的目录。
- 下面四行即为bash命令，设置好就会自动执行。

注意：
> 上述文件出现的`/var/www`为根目录，这里是我个人配置。供参考，具体自行修改设置。

#### 修改目录权限
```bash
$ chmod +x post-receive
$ chmod 777 -R /var/www/blog
```

### 第三步，修改本地博客配置
打开项目文件，找到`_config.yml`打开，找到`deploy`配置进行修改。
```
deploy:
  type: git
  message: update pages
  repo: username@xx.xx.xxx.xx:/var/www/blog.git
  branch: master
```
这里的`repo`配置是服务器地址配置。冒号后面对应的是上一步设置的仓库目录地址。`branch`是git分支。

修改好后执行`hexo g`进行编译，再执行`hexo d`进行部署。

提示输入密码，这里输入服务器登录密码即可。出现以下信息部署完成：
```
Branch 'master' set up to track remote branch 'master' from 'xx@xx.xx.xxx:/var/www/blog.git'.
INFO  Deploy done: git
```

The End😀
