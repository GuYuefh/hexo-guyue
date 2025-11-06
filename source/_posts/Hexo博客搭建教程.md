---
title: Hexo博客搭建教程
date: 2025-6-18 8:43:27
tags:
  - 开始
categories:
  - 教程
---

## 一、环境准备

###
1. Node.js 安装
Node.js 是 Hexo 的运行环境，必须先安装。

I、[前往官网下载](https://nodejs.org/en)
II、默认选项安装
III、打开命令提示符(CMD)验证安装:

``` bash
$ node -v
# 检查 Node.js 版本
```

返回版本信息则代表安装成功！

然后进行npm换源，运行

``` bash
$ npm config set registry https://registry.npmmirror.com
```
无报错则安装完成！

###
2. Git 安装

I、下载 [Git](https://git-scm.com/downloads)
II、安装时选择默认选项
III、验证安装:
``` bash
$ git --version
```
###
3. 安装 Hexo

[Hexo官网](https://hexo.io/zh-cn/)

在所有应用中打开安装好的 Git Bash 运行

``` bash
$ npm install -g hexo-cli
```

进行安装，之后运行

``` bash
$ hexo -v
```

验证是否安装成功

###
4. GitHub 部署
注册后创建仓库名格式必须为：<用户名>.github.io

最好创建成公开库

Git Bash 运行

``` bash
$ git config --global user.name <你的用户名>
$ git config --global user.email <你的邮箱>
```

运行以下代码检查是否配置成功

``` bash
$ git config -l
```

###
5. 连接至 GitHub
接着运行

``` bash
$ ssh-keygen -t rsa -C <你的邮箱>
```

直接按几次回车生成ssh密钥，用于此电脑连接至 GitHub

之后打开C盘用户文件夹下的.ssh的文件夹，用记事本打开 id_rsa.pub，复制里面的内容

然后点右上角头像 > Settings > SSH and GPG keys > New SSH key

Title随意，Key粘贴刚刚复制的密钥，之后点Add SSH key

运行以下代码测试连接，出现连接到账户至此环境部署完成

``` bash
$ ssh -T git@github.com
```

## 二、新建 Hexo 项目
在桌面或者其他文件夹下右键，Open Git Bash here，运行

``` bash
$ hexo init <项目名>
# 进入刚刚创建的项目
$ cd <项目名>
```

安装依赖

``` bash
$ npm i
```

## 三、配置 Hexo
请参考官方[配置文档](https://hexo.io/zh-cn/docs/configuration)

建议使用 Visual Studio Code 进行编辑[（点这里进行下载）](https://code.visualstudio.com/Download)

安装后并配置完成
打开项目文件夹，终端 > 新建终端，运行

``` SHELL
$ hexo cl; hexo g; hexo s
```
CTRL+鼠标打开 http://localhost:4000/ 测试网站
CTRL+C 可结束运行

## 四、安装主题
推荐主题 butterfly [安装及配置](https://butterfly.js.org/posts/21cfbf15/)

请认真阅读初始文档，完成安装和配置

## 五、托管到 GitHub
安装 hexo-deployer-git

``` SHELL
$ npm install hexo-deployer-git --save
```

修改 _config.yml 文件 deploy 部分

``` YAML
deploy:
  type: git
  repository: git@github.com:<用户名>/<用户名>.github.io.git
  branch: main
```

修改好配置后记得 CTRL+S 保存，运行以下命令，将代码部署到 GitHub

``` SHELL
$ hexo cl; hexo g; hexo d
```

如果出现Deploy done，则说明部署成功

## 六、部署到 Vercel
[官网地址](https://vercel.com/)

使用 GitHub 注册并登录，选择 Add New > Project

找到之前创建的库，点后面的 Import，直接点 Deploy 等待部署完成

之后到 Project 页面 > Domains 添加自己的域名，在域名管理页解析即可通过域名访问了！

建议购买自己的域名，推荐阿里云。


## 总结
完成以上步骤后，您的 Hexo 博客就基本搭建完成了！主要实现了:

基础环境配置
Hexo 框架安装
GitHub Pages 部署
主题美化