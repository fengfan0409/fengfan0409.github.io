#基于GitHub搭建自己的博客
##搭建环境准备
- Node.js 的安装和准备 
- Git的安装和准备 
- gitHub账户的配置

###Node.js 的安装和准备 

- 1.下载node.js安装文件：https://nodejs.org/en/
- 2.cmd，打开命令行界面,查看安装版本

```
nede -v
npm -v
```
###配置Git环境
- 下载Git安装文件：https://git-scm.com/downloads
- 打开命令行输入,检查安装是否成功

```
git --version
```
###github账户的注册和配置
- Github注册：https://github.com/
- 创建代码库：
- 在Repository name下填写yourname.github.io，Description (optional)下填写一些简单的描述（不写也没有关系

```
注意：
比如我的github名称是mengqian1117 ,
这里你就填 mengqian1117.github.io
```
- 代码库设置:Setting
   + 接下来开启gh-pages功能，点击界面右侧的Settings，你将会打开这个库的setting页面，向下拖动，直到看见GitHub Pages
   + 点击Automatic page generator，Github将会自动替你创建出一个gh-pages的页面
   
##安装Hexo
- 首先在E盘目录下创建Hexo文件夹，并在命令行的窗口进入到该目录

```
E:    进入E盘
cd Hexo 进入Hexo文件夹

```
- 安装HEXO

```
npm install hexo-cli -g
```
可能你会看到一个WARN，但是不用担心，这不会影响你的正常使用。 然后输入

- 保存hexo

```
npm install hexo --save
```
- 检查安装是否成功

```
hexo -v
```
##hexo的相关配置
###初始化Hexo

```
hexo init
npm install
```
###首次体验Hexo

```
hexo g   #生成
hexo s   #启动服务
```
在浏览器中打开http://localhost:4000/
##怎样将Hexo与github page 联系起来
大概分为以下几步
 
- 配置git个人信息 
- 配置Deployment

###配置Git个人信息
- 1.设置Git的user name和email：(如果是第一次的话)

  ```
  git config --global user.name "mengqian1117"
  git config --global user.email "mengqian1117@163.com"
  ```
- 2.检查是否已经有SSH Key。
  ```
  cd ~/.ssh
  ls
  ```
- 3.生成密钥
  ```
  ssh-keygen -t rsa -C "mengqian1117@163.com"
  ```
  
  ```
  连续3个回车。如果不需要密码的话。
  最后得到了两个文件：id_rsa和id_rsa.pub。
  默认的存储路径是：C:\Users\Administrator\.ssh
  ```
- 4.添加密钥到ssh-agent
  
  ```
  eval "$(ssh-agent -s)"
  ```
  添加生成的 SSH key 到 ssh-agent。
  
  ```
  ssh-add ~/.ssh/id_rsa
  ```
- 5.登陆Github, 添加 ssh 
  把id_rsa.pub文件里的内容复制到SSH keys
- 6.测试：
  
  ```
  ssh -T git@github.com
  ```
  你将会看到：如果看到Hi后面是你的用户名，就说明成功了。
  
  ```
  如果提示Are you sure you want to continue connecting (yes/no)?，输入yes
  ```
###配置Deployment
- 配置_config.yml中有关deploy的部分：
  
  ```
  deploy:
  type: git
  repository: git@github.com:mengqian1117/mengqian1117.github.io.git
  branch: master

  ```
##写博客、发布文章
- 1.定位到我们的hexo根目录，执行命令：
  
  ```
  hexo new 'my-first-blog'
  ```
- hexo会帮我们在_posts下生成相关md文件,用马克飞象打开写文章就可以
- 文章编辑好之后，运行生成、部署命令：
  
  ```
  hexo g   // 生成
  hexo d   // 部署
  ```
  或者
  
  ```
  hexo d -g #在部署前先生成
  ```
###踩坑提醒
```
deloyer not found:git
```
 这样的错误是需要装插件
 
 ```
 npm install hexo-deployer-git --save
 ```
 
 hexo
npm install hexo -g #安装  
npm update hexo -g #升级  
hexo init #初始化
简写
hexo n "我的博客" == hexo new "我的博客" #新建文章
hexo p == hexo publish
hexo g == hexo generate#生成
hexo s == hexo server #启动服务预览
hexo d == hexo deploy#部署

服务器
hexo server #Hexo 会监视文件变动并自动更新，您无须重启服务器。
hexo server -s #静态模式
hexo server -p 5000 #更改端口
hexo server -i 192.168.1.1 #自定义 IP

hexo clean #清除缓存 网页正常情况下可以忽略此条命令
hexo g #生成静态网页
hexo d #开始部署

监视文件变动
hexo generate #使用 Hexo 生成静态文件快速而且简单
hexo generate --watch #监视文件变动

完成后部署
两个命令的作用是相同的
hexo generate --deploy
hexo deploy --generate
hexo deploy -g
hexo server -g

草稿
hexo publish [layout] <title>

模版
hexo new "postName" #新建文章
hexo new page "pageName" #新建页面
hexo generate #生成静态页面至public目录
hexo server #开启预览访问端口（默认端口4000，'ctrl + c'关闭server）
hexo deploy #将.deploy目录部署到GitHub

hexo new [layout] <title>
hexo new photo "My Gallery"
hexo new "Hello World" --lang tw

变量	描述
layout	布局
title	标题
date	文件建立日期
title: 使用Hexo搭建个人博客
layout: post
date: 2014-03-03 19:07:43
comments: true
categories: Blog
tags: [Hexo]
keywords: Hexo, Blog
description: 生命在于折腾，又把博客折腾到Hexo了。给Hexo点赞。
模版（Scaffold）
hexo new photo "My Gallery"

变量	描述
layout	布局
title	标题
date	文件建立日期
设置文章摘要
以上是文章摘要 <!--more--> 以下是余下全文 
写作
hexo new page <title>
hexo new post <title>

变量	描述
:title	标题
:year	建立的年份（4 位数）
:month	建立的月份（2 位数）
:i_month	建立的月份（去掉开头的零）
:day	建立的日期（2 位数）
:i_day	建立的日期（去掉开头的零）
推送到服务器上
hexo n #写文章
hexo g #生成
hexo d #部署 #可与hexo g合并为 hexo d -g