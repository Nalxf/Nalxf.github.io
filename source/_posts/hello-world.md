---
title: Hexo+github+node.js 配置的个人博客终于完成了
date: 2017/8/07 11:18:25
categories:
- 随笔
tags:
- 心情
- Hexo 初步了解
description: 希望自己能 力学笃行 不断前进。
---

个人博客在看了网上各种风格的教程,终于是建立起来了.
Hexo API 常用命令整理.

# 代码块
## 生成新文章：路径(source /_posts / title.md)
```
hexo new "title"
```

### 生成新的页面，后面可在主题配置文件中配置页面
```
hexo new page "title"
```

## 在文章中插入代码。 code

```
{% codeblock [title] [lang:language] [url] [link text] %}
code snippet
{% endcodeblock %}

{% codeblock %}
alert('Hello World!');
{% endcodeblock %}
````
# iframe
## 在文章中插入 iframe。
```
{% iframe url [width] [height] %}
```
# Image
# 在文章中插入指定大小的图片。
```
{% img [class names] /path/to/image [width] [height] [title text [alt text]] %}
```
# Link
## 在文章中插入链接，并自动给外部链接添加 target="_blank" 属性。
```
{% link text url [external] [title] %}
```
# Vimeo
## 在文章中插入 Vimeo 视频。
```
{% vimeo video_id %}
```














































<!--
原始文件 存档

Welcome to [Hexo](https://hexo.io/)! This is your very first post. Check [documentation](https://hexo.io/docs/) for more info. If you get any problems when using Hexo, you can find the answer in [troubleshooting](https://hexo.io/docs/troubleshooting.html) or you can ask me on [GitHub](https://github.com/hexojs/hexo/issues).

## Quick Start

### Create a new post

``` bash
$ hexo new "My New Post"
```

More info: [Writing](https://hexo.io/docs/writing.html)

### Run server

``` bash
$ hexo server
```

More info: [Server](https://hexo.io/docs/server.html)

### Generate static files

``` bash
$ hexo generate
```

More info: [Generating](https://hexo.io/docs/generating.html)

### Deploy to remote sites

``` bash
$ hexo deploy
```

More info: [Deployment](https://hexo.io/docs/deployment.html)
 -->



