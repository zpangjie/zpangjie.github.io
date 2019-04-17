---
title: 用GitHub+hexo创建个博客
categories: 计算机&编程
tags:
- 计算机&编程
- 博客

---

## O 踩了N多坑总结出以下经验
**一步一步绝对能成 mac+windows**
<!-- more -->
## 一 常见有三种博客搭建方案

- [workpress](https://zh-cn.wordpress.com/)

> 一般需要独立域名(充钱)有广告，做许多东西需要升级至高级版(还是充钱)，手机版访问麻烦(所以我直接扔了那个博客)

- [GitHub](https://github.com/) + [jekyll](https://jekyllrb.com/)

> 稍微麻烦一点 (其实是作者技术太挫)
 
- [GitHub](https://github.com/) + [Hexo](https://hexo.io/zh-cn/)

![C位当然要有配图](https://user-images.githubusercontent.com/48438858/54468954-e73dd380-47cc-11e9-8089-a1f910273b15.png)



> 免费 简单 据说用的人还多 所以我选择这个

## 二 下面直接进入主题 👇 博客搭建

#### 首先我们需要一个[GitHub](https://github.com/)账号和一个项目库

怎么创建账号就不用我说了，但是创建库的时候需要提到一个细节

1 先点击这里创建

![点击创建项目](https://user-images.githubusercontent.com/48438858/54468995-6cc18380-47cd-11e9-8290-c0727beb3fa5.png)

2 创建项目的是时候Repositoryname需要同Owner一样然后补齐github.io

![设置仓库名](https://user-images.githubusercontent.com/48438858/54469009-adb99800-47cd-11e9-8a87-7e05fd3b80e6.png)

3 然后点击 Create repository创建就好

## 三 环境配置

[Hexo](https://hexo.io/docs/)有着详细的安装使用介绍 下面是我的

### 先怼node,js

mac: 去[Node.js](https://nodejs.org/en/)官网，我下载了左边的那个 然后一路安装即可

windows: [Node.js](https://nodejs.org/en/download/)下载windows就可以
下载安装包，安装Node.js会包含环境变量及npm的安装，安装之后可以在命令行中输入node -v看看是否安装成功。

如果 git bash 里报错了，就去环境变量里看看有没有 nodejs，没有的话需要把nodejs地址添加一下如果已经有了，重启电脑。

### 再怼git

mac: [点击这里进入页面自动下载了](https://www.git-scm.com/download/mac)

windows: [点击这里进入页面直接下载了](https://git-scm.com/download/win)记得git -v 查看是否安装成功失败了请参看其他详细git安装教程(我反正没失败过)

### 然后就可以安装Hexo了 
#### mac:

  Node.js和Git都安装好后就可以安装Hexo了。
  
  终端执行怼下命令： sudo npm install -g hexo
  
  *如果需要输入密码就是Mac登录密码*
  
  这里就是一个大坑：Hexo官网上的安装命令是 npm install -g hexo-cli，多数教程也都是没有sudo然鹅直接怼就去就会报错权限，加sudo解决问题。
  
#### windows:  

npm install -g hexo-cli

### 将你的git与GitHub绑定
#### 由于Git是分布式版本控制系统，所以，每个机器都必须自报家门：你的名字和Email地址

git config --global user.name "你的GitHub用户名"

git config --global user.email "你的GitHub注册邮箱"
#### 生成ssh密钥

生成密钥 输入： ssh-keygen -t rsa -C "你的GitHub注册邮箱"
然后回车遇到y or n? 就y 继续回车

mac: 先输入 cd ~

然后就可以cd~/.ssh 里面会有id_rsa和rsa_rsa.pub两个文件

vim rsa_rsa.pub复制里面的内容 没有vim的话vi应该有用vi rsa_rsa.pub

windows:

输入ls -a 查看所有文件 在输入cat.ssh\id_rsa.pub打开文件

复制里面全部内容


然后打开git设置(点击头像 seeings)

![配置新的ssh](https://user-images.githubusercontent.com/48438858/54468999-7cd96300-47cd-11e9-912c-6876d0a52614.png)

然后粘贴你的密钥 Add SSH key保存

![加入密钥保存](https://user-images.githubusercontent.com/48438858/54469020-c924a300-47cd-11e9-9bf0-aa23bca3afa0.png)


## 部署

#### mac

我们先找个地方创建一个文件夹这里会存放你的blog(博客)全部内容

打开终端进入这个文件夹目录 blog是你的文件夹名称

输入hexo init blog

然后cd到blog文件夹下安装npm

输入 npm install

执行下面的命令开启hexo服务器

输入 hexo s

这个时候你可以看见一个这样的博客页面了打开浏览器

输入 localhost:4000

#### 接下来就是部署了

首先介绍一下两个配置文件他们都叫_config.yml

不同的是blog里面的_config.yml是站点配置文件

而我们themes文件夹每个主题文件里也有一个_config.yml他是配置主题的文件

我们打开blog里面的_config.yml 输入vim _config.yml

翻到最下面改成这样没有就加上

![这样](https://user-images.githubusercontent.com/48438858/54469024-d477ce80-47cd-11e9-91af-e0396018de5f.png)

你的地址在这里

![在这里](https://user-images.githubusercontent.com/48438858/54469027-e22d5400-47cd-11e9-8287-602cc4544dc8.png)

这里需要注意坑二 每一个配置的 ： 后面要有一个空格！！！！
然后保存站点配置

在blog文件夹目录里面执行一下生成静态页面命令

输入 hexo g  (或是hexo generate)

如果有报一下错误

注：save前面的-是两个被浏览器自动处理成一个了请手动添加上去(不然会报错)
>ERROR Local hexo not found in ~/blog

>ERROR Try runing: 'npm install hexo --save'

就执行 输入 npm install hexo --save
没有报错请不要执行或者忽略

执行配置命令``

hexo d  (或是 hexo deploy)

这里特别注意 我就是载在这里！ 若执行命令hexo deploy仍然报错：无法连接git或找不到git，则执行如下命令来安装一个叫hexo-deployer-git东西

>输入 npm install hexo-deployer-git --save

执行 hexo g
执行 hexo d

倘若提示输入密码输入即可没有执行忽略

这时候就可以访问你的博客了   https://写你的.github.io/

### 发布文章

终端cd到blog文件夹目录 

输入hexo new "文件名" 新建文章

#### 发布部署
然后 hexo g (生成静态页面)
在然后 hexo d (部署到github)

如果出现了花里胡哨的错误可以在生成之前

输入 hexo clean

ps: 每次更新都会等那么一会

## 写下更换主题吧

在[hexo主题](https://hexo.io/themes/)里找到一款主题我的是yilia

下载这个主题

输入 git clone https://github.com/litten/hexo-theme-yilia.git themes/yilia

![这里会多一个](https://user-images.githubusercontent.com/48438858/54469036-f1ac9d00-47cd-11e9-8484-ecb7ef4a6f84.png)
> ``
打开站点的_config.yml配置文件，将里面的 theme: landscape 改为 theme: yilia.

![改成你主题的名字](https://user-images.githubusercontent.com/48438858/54469042-fbce9b80-47cd-11e9-95d9-cc2677a64899.png)


然后还是 hexo g 和 hexo d

最后访问下你的博客吧这里在看看扔出我的

[张胖杰的博客](https://zpangjie.github.io/)

ps: 每次更新都会等那么一会!!!!!!!!





  













