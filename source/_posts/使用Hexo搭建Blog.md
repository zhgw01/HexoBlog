---
title: 使用Hexo搭建Blog
date: 2016-02-03 15:41:12
toc: true
categories: [杂七杂八]
tags: [hexo,github]
---

# 安装Hexo

Hexo 是一个快速、简洁且高效的博客框架， 使用MarkDown解析文章，通过配合主题使用，可以生成漂亮的静态网页，托管在Github上

在安装hero，需要先安装以下的依赖

* node.js
* git

假设你已经安装了上面的一些东西，那么可以直接开始安装hexo。

``` shell
 npm install -g hexo-cli
```

一条命令就搞定了，如果在国内，将`npm`替换为`cnpm`，可以大大提高速度

# 使用Hexo初始化博客目录

安装Hexo后，就可以快速初始化一个项目文件。

``` shell
hexo init <folder>
cd <folder>
npm instal
```

以下假设你希望初始化一个blog的文件夹，那么可以这么做

``` shell
hexo init blog
cd blog
npm install
```

初始化后，你会在blog底下看到如下的目录结构

``` shell
.
├── _config.yml
├── package.json
├── scaffolds
├── source
|   ├── _drafts
|   └── _posts
└── themes
```

其中最重要的就是`_config.yml`, 它是用来配置你的站点的主要信息。*注意`：`后面必须跟个空格*

首先是博客站点的基本信息

``` shell
title: 站点名字
subtitle: 子标题
description: 描述
author: 作者
language: zh-CN
timezone: Asia/Shanghai
```

配置完博客的基本信息，就是配置博客最终发布的url

``` shell
url: http://lyallchan.github.io
root: /
permalink: :year/:month/:day/:title/
```

如果你的博客部署在站点的子目录下，比如http://yourhost.com/blog, 则root指向blog这个subfolder

``` shell
url: http://yourhost.com
root: /blog/
permalink: :year/:month/:day/:title/
```

最后如果使用github page来托管博客的话，可以配置如下的部署

``` 
deploy:
  type: git
  repo: git@github.com:lyallchan/lyallchan.github.io.git
```

# 安装[maupassant](https://www.haomwei.com/technology/maupassant-hexo.htm)主题

maupassant是一个很清爽的主题，下面介绍了在Hexo如何使用新的主题

``` sh
cd ~/blog
git clone https://github.com/tufu9441/maupassant-hexo.git themes/maupassant
npm install hexo-renderer-sass --save
npm install hexo-renderer-jade --save
```

修改`~/blog/_config.yml`的theme配置，使得maupassant主题生效

``` 
theme: maupassant
```

maupassant也有自己的配置文件`themes/maupassant/_config.yml`, 具体参考[maupassant 配置](https://www.haomwei.com/technology/maupassant-hexo.html)

注意，你必须运行`hexo g`来生成静态页，才能看到新的效果，否则有可能发现样式错乱。

# 生成一篇新文章

可以简单生成如下

``` shell
cd ~/blog
hexo new blog_name
vim source/_posts/blog_name.md 
```

# 生成跟预览

在预览前，你先需要生成静态文件出来

``` shell
hexo g
```

生成完后，可以在本地用hexo启动一个服务器，看看效果

``` 
hexo s
```

在浏览器里面查看http://localhost:4000 就可以查看效果了

# 部署

最后自然是部署了，可以加一个参数，要求生成后再部署

``` shell
hexo deploy --generate
```

# 其余

待续

# 参考

* [Hexo](https://hexo.io/docs/index.html)
  
* https://www.haomwei.com/technology/maupassant-hexo.html
  
* http://lyallchan.github.io/2015/12/10/%E5%AE%89%E8%A3%85%E5%92%8C%E9%85%8D%E7%BD%AEnvm%E3%80%81nodejs%E5%92%8Chexo/
  
* http://www.wisedream.net/2016/01/08/hexo-custermize/
  
  ​