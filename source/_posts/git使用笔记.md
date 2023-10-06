---
title: git使用笔记
date: 2023-09-29 09:48:32
tags:
- git
categories:
- git
keyword:
- git
cover: 
---

>当在多个电脑上协同工作时，我们不免用到版本控制系统，版本控制系统分为分布式与集中式。
>集中式版本控制系统的代码存放在中央仓库，用的时候需要先拉取并且一直保持联网才能使用，常见的有`CVS`与`SVN`。
>分布式版本控制系统的代码存放在中央仓库与每个人的电脑中，因此也比较安全，常见的有`git`。
>`git`是世界上最先进的版本控制系统，有强大的分支管理功能。

### git的安装和配置
#### 下载与安装
##### Windows
进入官网：(https://git-scm.com/downloads)下载安装包安装。
由于官网下载太慢可以通过淘宝的开源镜像下载 网址：https://registry.npmmirror.com/binary.html?path=git-for-windows/v2.36.1.windows.1/ ，下载版本更具自己的需求选择即可。
##### Ubuntu/Debian
```shell
$ apt-get install libcurl4-gnutls-dev libexpat1-dev gettext libz-dev libssl-dev

$ apt-get install git

$ git --version
git version 1.8.1.2
```
##### Centos
```shell
$ yum install curl-devel expat-devel gettext-devel openssl-devel zlib-devel

$ yum -y install git-core

$ git --version
git version 1.7.1

```
:::tip
安装完右击即可看见三个选项
* Git CMD 是windows 命令行的指令风格
* Git Bash 是linux系统的指令风格（建议使用）
* Git GUI是图形化界面（新手学习不建议使用）
:::


#### 设置全局身份
右键打开Git Bash，设置用户名和邮箱
```shell
$ git config --global user.name "你的用户名"
$ git config --global user.email "你的邮箱"
```
:::tip
如果用了 --global 选项，那么更改的配置文件就是位于你用户主目录下的那个，以后你所有的项目都会默认使用这里配置的用户信息。

如果要在某个特定的项目中使用其他名字或者电邮，只要去掉 --global 选项重新配置即可，新的设定保存在当前项目的 .git/config 文件里。
:::

:::tip
通过git config -l 检查是否配置成功，至此git安装及配置全部完成。
```shell
$ git config --list
```
:::

#### 生成密钥
```shell
$ ssh-keygen -t rsa -C "邮箱名称"
```
:::tip
生成过程中有设置密码的环节，无需设置密码可直接回车
生成成功后私钥和公钥存在于用户目录的.ssh中。
:::

私钥存放在`C:\Users\16475\.ssh\id_rsa.pub`中，用记事本打开复制内容粘贴到剪贴板。
进入github，点击右上角头像 选择`settings`，进入设置页后选择 `SSH and GPG keys`，名字随便起，公钥填到`Key`那一栏。

:::tip
测试连接，输入以下命令:
```shell
ssh -T git@github.com
```
出现连接到账户的信息，说明已经大功告成，至此完成了环境准备工作。
:::

### 使用git
#### git使用流程

:::tip
(初始化仓库 ->添加远程仓库)/ (克隆远程仓库到本地) ->添加文件到本地分支->将文件发送到暂存区 ->将文件提交到代码仓库
:::

##### 初始化git仓库
```shell
$ git init
```

##### 添加远程仓库
:::tip 列出当前仓库中已配置的远程仓库，并显示它们的 URL。
```shell
$ git remote -v
```
:::
github仓库名    git@github.com:Jeafly/Jeafly.github.io.git URL
```shell
$ git remote add github git@github.com:Jeafly/Jeafly.github.io.git
```

##### 将本地文件夹下的文件添加到本地分支
```shell
$ git add .
```

##### 将文件存储到暂存区
```shell
$ git commit -m [message]
```

##### 将文件提交到远程仓库
```shell
$ git push <远程主机名> <本地分支名>(:<远程分支名>)
```

##### 克隆远程仓库到本地
```shell
$ git clone [url]
```
