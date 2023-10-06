---
title: Hexo博客的搭建教程(一)
date: 2023-10-05 22:01:31
tags: Hexo
cover: 
---

### 环境搭建
* 操作系统：Win11
* Node.js
* Git
* Hexo

### 安装Node.js
1. 打开Node官网，下载和自己系统相配的Node的安装程序，否则会出现安装问题。下载地址：https://nodejs.org/en/download/
我个人的版本是 12.19.0，目前版本已经更新到19.0.0，按照个人经验，可以选个低一些的版本，可以和我的一样，否则后面会出现各种不兼容的问题！我之前就是安装16的，系统无法识别，如果大家遇到问题建议选个低版本的！历史版本下载页面：https://nodejs.org/en/download/releases/
2. 下载后安装，安装的目录可以使用默认目录【C:/Program Files/nodejs/】，也可以自定义路径。
这个环境路径切换坑也很多，如果大家C盘空间足够可以直接装C盘，如果想切换其他盘或者把环境遍历切换到自定义路径也可以，具体教程百度(不过坑比较多就是了)!
3. 安装完成后，检查是否安装成功。在键盘按下win + R键，输入CMD，然后回车，打开CMD窗口，执行node -v命令，看到版本信息，则说明安装成功。
4. 修改npm源。npm下载各种模块，默认是从国处服务器下载，速度较慢，建议配置成`淘宝镜像`。打开CMD窗口，运行如下命令:
```shell
npm config set registry https://registry.npm.taobao.org
```
### 安装Hexo
1. 在`Git BASH`输入如下命令安装
```shell
npm install -g hexo-cli
```

2. 安装完后输入hexo -v验证是否安装成功。

### 创建仓库
1. 登录Github，点击右上角的+按钮，选择New repository，创建一个<用户名>.github.io的仓库。
2. Description：为描述仓库（选填）
3. 勾选 Initialize this repository with a README 初始化一个 README.md 文件
4. 点击 Creat repository 进行创建

### 安装Git
参考这边文章：

### 初始化Hexo项目
1. 在目标路径（我这里选的路径为【D:\新建文件夹\blog】）打开cmd命令窗口，执行hexo init初始化项目。
```shell
hexo init blog(项目名)
```

2. 进入`blog`，输入`npm install`(`npm i`)安装相关依赖。
```shell
cd blog  //进入blog文件夹
npm install
```

3. 初始化项目后，blog-demo有如下结构：
【node_modules】：依赖包
【scaffolds】：生成文章的一些模板
【source】：用来存放你的文章
【themes】：主题
【.npmignore】：发布时忽略的文件（可忽略）
【_config.landscape.yml】：主题的配置文件
【config.yml】：博客的配置文件
【package.json】：项目名称、描述、版本、运行和开发等信息

4. 输入`hexo server`(`hexo s`)启动项目

5. 打开浏览器，输入地址：`http://localhost:4000/` ，看到下面的效果，说明你的博客已经构建成功了。

### 将静态博客挂载到 GitHub Pages
1. 安装 hexo-deployer-git
```shell
npm install hexo-deployer-git --save
```

2. 修改 _config.yml 文件
在blog-demo目录下的_config.yml，就是整个Hexo框架的配置文件了。可以在里面修改大部分的配置。详细可参考官方的[配置描述](https://hexo.io/zh-cn/docs/configuration)。
修改最后一行的配置，将repository修改为你自己的github项目地址即可，还有分支要改为main代表主分支（注意缩进）。
```yaml
deploy:
  type: git
  repository: git@github.com:Jeafly/Jeafly.github.io.git
  branch: main
```

3. 修改好配置后，运行如下命令，将代码部署到 GitHub（Hexo三连）。
```shell
hexo clean && hexo generate && hexo deploy  // Git BASH终端
hexo clean; hexo generate; hexo deploy  // VSCODE终端(PowerShell)
```
* hexo clean：删除之前生成的文件，若未生成过静态文件，可忽略此命令。
* hexo generate：生成静态文章，可以用hexo g缩写
* hexo deploy：部署文章，可以用hexo d缩写

:::tip
注意：deploy时可能要你输入 username 和 password。
:::
如果出现Deploy done，则说明部署成功了。

稍等两分钟，打开浏览器访问：https://Jeafly.github.io ，这时候我们就可以看到博客内容了。

>无法连接github的解决方案
>1. 挂代理或者加速器
>2. 修改Host文件，可以参考开源项目[Github520](https://github.com/521xueweihan/GitHub520)




