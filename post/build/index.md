# 一、安装Hugo 
 
> Install Hugo on macOS, Windows, Linux, FreeBSD, and on any machine where the Go compiler tool chain can run.  
Hugo是前Docker职员 Steve Francia 开发的基于golang的开源静态站点生成工具，  
官方主页：https://gohugo.io/。

> 安装方式有多种，Mac下可通过brew安装。
  
  ```sh
$ # brew install hugo  
$ # which hugo
    /usr/local/bin/hugo
```

# 二、生成静态站点

### 1.创建站点

```sh
$ # hugo new site blog
   Congratulations! Your new Hugo site is created in ...
$ # tree
 .
 └── blog
     ├── archetypes  //存放default.md，头文件格式
     ├── config.toml //配置文件
     ├── content  //博客文章
     ├── data   //自定义模版等
     ├── layouts  //模板文件
     └── static   //静态资源
```
启动站点：  
```sh
$ # hugo server
                   | EN  
+------------------+----+
  Pages            |  8  
  Paginator pages  |  0  
  Non-page files   |  0  
  Static files     | 23  
  Processed images |  0  
  Aliases          |  1  
  Sitemaps         |  1  
  Cleaned          |  0  
  Web Server is available at http://localhost:1313/ (bind address 127.0.0.1)
  Press Ctrl+C to stop
```
这样，一个站点就建好了，本地直接访问http://localhost:1313。 
 
### 2.theme选择
 Hugo官方主题：https://themes.gohugo.io/。  
 选好主题后从gitHub下载下来，将解压出的文件放到themes文件夹下。  
 这里，本站的选择是[hugo-theme-even](https://github.com/olOwOlo/hugo-theme-even/blob/master/README-zh.md)主题。  
 Installation
 
```sh
git clone https://github.com/olOwOlo/hugo-theme-even themes/even
```
Configuration  
将 ```exampleSite```目录下的 ```config.toml``` 文件复制到你的站点目录，根据需求进行更改即可。

### 3.发表文章
博客默认没有文章，可使用````hugo new```来生成。  
```sh
$ # hugo new post/about.md
...post/about.md created
```
使用markdown编辑器打开文件 post/about.md编辑  
```
title: "about"
date: 2018-01-06T19:58:40+08:00
Tags: ["about"] //标签
Categories : ["about"] //分类
...
...这里是正文
...

```

### 4.部署到github
先在GitHub上创建一个由你昵称命名的```Repository```拉到本地，然后pubilc目录里所有文件 ```push```到刚建的那个```Repository```的```master```分支。  

附： 
绑定自己域名：    
在自己的域名解析页面添加一条  
CNAME记录类型：绑定Github提供的二级域名。  
然后在```Repository```的setting里面绑定Custom domain即可。
