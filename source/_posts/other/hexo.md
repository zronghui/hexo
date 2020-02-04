---
title: hexo
date: 2019-08-29 19:05:31
categories: []
tags: [hexo]
# password: 1
---
<!--toc-->
<!--more-->
# hexo 安装、使用

## 安装

见

<a>https://wuzequn.com/2018/04/27/blog-build-and-ipv6-tools</a>

<a>http://www.dragonbaby308.com/hexo</a>

<!--more-->

## 初始化项目

hexo init blog

## 配置

修改 bog 项目下的\_config.yml 文件，D:\01 Code\hexo_config.yml
language: zh-Hans

## 使用

### 创建新文章

hexo new new-article

### 重新发布

hexo clean;hexo g;hexo s

hexo clean

hexo generate 或 hexo g

hexo server 或 hexo s

## 部署到 github

<blockquote>
服务器部署
（一） 本地 + github.io 白嫖部署

1. 生成 github.io 仓库
   首先注册并登录 GitHub，创建新 public 仓库，仓库名称一定要是：
   YourGitHubName.github.io（YourGitHubName 是你的 GitHub 昵称，大小写敏感！）

2. 本地安装 Hexo 的 git 部署插件
   在 Hexo 的目录下，输入 npm install --save hexo-deployer-git，会报一个 peerDependencies WARNING，可以忽略。

3. 本地修改\_config.yaml 文件
   在 Hexo 目录下，找到\_config.yaml 文件，在#Deployment 做如下修改：

<html>
    <title>Markdown</title>

    # Deployment
    ## Docs: https://hexo.io/docs/deployment.html
    deploy:
    type: git
    repo: https://github.com/DragonBaby308/DragonBaby308.github.io.git #你的 github.io 的网址
    branch: master #“type:”、“repo:”和“branch:”后都要带一个空格

</html>

4. 部署
   hexo d
   部署成功后，浏览器输入 YourGitHubName.github.io 即可访问，其中 YourGitHubName 是你的 GitHub 昵称，且大小写敏感
   见
   </blockquote>

详见

<a>http://www.dragonbaby308.com/hexo/</a>

## 发布

hexo clean;hexo g;hexo d

输入 github 账号名，密码

hexo d 即 hexo deploy

## 其他配置

Hexo+Next 个人博客主题优化 - 简书
https://www.jianshu.com/p/efbeddc5eb19

主要配置了：

![20190829215100.png](https://i.loli.net/2019/08/29/sE5TD1lwjCId7ue.png)

Hexo 之 next 主题设置首页不显示全文(只显示预览) - 简书
https://www.jianshu.com/p/393d067dba8d

Hexo+Next个人博客主题优化 - 简书
https://www.jianshu.com/p/efbeddc5eb19

Dragonstyle's Home – 记录、分享、交流
http://www.dragonstyle.win/

### 修改文章宽度

https://ihaoming.top/archives/9a935f57.html

### deploy 免账号密码

> 可将\_config.yml 中的 repo 修改为如下标准格式：
> repo: https://用户名:密码@github.com/用户名/用户名.github.io.git
> 这样做的好处就是每次 hexo deploy 提交时不需要输入账号密码。

### hexo的首页只显示文章的部分内容
[让hexo的首页只显示文章的部分内容而不是全部 | 朱启的个人博客](http://blog.smallerpig.com/set-hexo-show-more-button-on-indexpage.html)

``` 
第二种方法

在你写 md 文章的时候，可以在内容中加上 <!--more-->，这样首页和列表页展示的文章内容就是 <!--more--> 之前的文字，而之后的就不会显示了。

效果

上面两种方式展示出来的效果是不一样的。

第一种修改 _config.yml 文件的效果是会格式化你文章的样式，直接把文字挤在一起显示，最后会有 …。

而第二种加上 <!--more-->展示出来的就是你原本文章的样式，最后不会有…
```

## 换电脑

见

<a>https://feijunjie.github.io/2018/10/10/20181010-%E5%A6%82%E4%BD%95%E5%9C%A8%E5%8F%A6%E4%B8%80%E5%8F%B0%E7%94%B5%E8%84%91%E4%B8%8A%E7%BB%A7%E7%BB%ADhexo%E5%86%99%E5%8D%9A%E5%AE%A2/</a>

## 注意事项
在标题开头使用如下形式
[精]精华文章
会报错

## 问题
### search一直加载
解决办法：
1. 查看search.xml的请求
2. 打开新窗口，直接访问xml网址，查看哪一行解析失败，回到请求页面，查看是哪个文件
3. 去vim查看异常字符

### 热度统计没生效
[Next 解决 Busuanzi 统计浏览失效 | G加菲](https://www.gmlyo.com/2018/12/02/Next-%E8%A7%A3%E5%86%B3-Busuanzi-%E7%BB%9F%E8%AE%A1%E6%B5%8F%E8%A7%88%E5%A4%B1%E6%95%88/)

### 文章置顶
[解决Hexo博客文章置顶问题 - 简书](https://www.jianshu.com/p/42a4efcdf8d7
)
### 侧边栏添加自定义文件夹
[【Hexo + Next】侧边栏添加自定义文件夹（如友链）_Spr Chan的博客-CSDN博客](https://blog.csdn.net/weixin_43971764/article/details/97644190)
### Archive页面显示文章数量
npm install hexo-generator-archive --save

_config.yml中新增相关配置
archive_generator:
  per_page: 40  #值为0表示不分页，按需填写
  yearly: true  #是否按年生成归档
  monthly: true  #按月归档
index_generator:
  per_page: 40  #值为0表示不分页，按需填写
  yearly: true  #是否按年生成归档
  monthly: true  #按月归档

tag_generator:
  per_page: 40  #值为0表示不分页，按需填写
  yearly: true  #是否按年生成归档
  monthly: true  #按月归档

category_generator:
  per_page: 40  #值为0表示不分页，按需填写
  yearly: true  #是否按年生成归档
  monthly: true  #按月归档

### EIO: i/o error
➜  hexo hexo d
INFO  Deploying: git
INFO  Clearing .deploy_git folder...
FATAL Something's wrong. Maybe you can find the solution here: https://hexo.io/docs/troubleshooting.html
Error: EIO: i/o error, stat '/Volumes/Data/01 Code/hexo/.deploy_git/2019'
➜  hexo open .
在finder中，删除文件夹
再hexo deploy

[hexo文章模板设置 | 拈花把酒偏折煞世人情狂](https://shmilybaozi.github.io/2018/11/05/hexo%E6%96%87%E7%AB%A0%E6%A8%A1%E6%9D%BF%E8%AE%BE%E7%BD%AE/)

[Hexo设置网站的图标Favicon | G加菲](https://www.gmlyo.com/2018/06/06/Hexo%E8%AE%BE%E7%BD%AE%E7%BD%91%E7%AB%99%E7%9A%84%E5%9B%BE%E6%A0%87Favicon/)
[在线免费将图片转换成ico图标格式-转换成ico](https://jinaconvert.com/cn/convert-to-ico.php)

# hexo中文版
![WqyrkmoDMjSlHY7](https://i.loli.net/2020/01/14/WqyrkmoDMjSlHY7.png)
![uro1ynZdBiXEHKp](https://i.loli.net/2020/01/14/uro1ynZdBiXEHKp.png)
![8Wu9HGLymK3Cw4O](https://i.loli.net/2020/01/14/8Wu9HGLymK3Cw4O.png)
![fWXaVcbtCg8kMNo](https://i.loli.net/2020/01/14/fWXaVcbtCg8kMNo.png)

[jaredly/hexo-admin: An Admin Interface for Hexo](https://github.com/jaredly/hexo-admin)