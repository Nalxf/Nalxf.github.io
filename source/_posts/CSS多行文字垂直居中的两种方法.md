---
title: CSS多行文字垂直居中的两种方法
date: 2017-08-23 14:05:04
categories:
- 随笔
tags:
- 整理总结
- css
---

#### 问题 : 让多行文字,在元素中垂直居中 ?

* 在一行问题的时候我们 可以 line-hanght 来设置垂直居中 ,但是多行的时候 , 就不行了
* 我们也可以用 padding 把上下的 距离撑开 实现上下居中
* 我们还可以使用 定位(position) 把元素的位置 移动 实现上下居中
* 用 js 来实现居中对齐
* 最简单的,最符合日常需求的?
* 不复杂,易维护,兼容好


![每天进步一点点](http://ou5ix7hfz.bkt.clouddn.com/t01c33d4326a1e51f9e.webp.jpg)
<!-- more -->

水平垂直居中，特别是使用在列表的时候经常会用到的，以前有需求的时候我也做过类似的代码，是使用display:table-cell
今天整理一下，并结合前人的辛劳，总结一下以作备份。
水平居中，如果知道元素的宽度，则可以使用

#### 先看看css水平居中
```
.cell{width:300px; margin:0 auto; text-align:center;}
```
如果是内联元素居中，那么直接用text-align:center则行
如果未知元素宽度，并且非内联元素，那么下面给出的几种方案也适合你。

#### 第一种：相对定位法
> 原理是父类浮动的同时向左left:50%,而子类则向右浮动的同时left:50%;

```
<style type="text/css">
.centerlist {position:relative;left:50%;float:left;}
.centerlist li {position:relative;right:50%; z-index:2;float:left}
</style>
<ul class="centerlist">
    <li><a href="#">Lorem ipsum dolor.</a></li>
    <li><a href="#">Lorem ipsum dolor.</a></li>
    <li><a href="#">Lorem ipsum dolor.</a></li>
    <li><a href="#">Lorem ipsum dolor.</a></li>
    <li><a href="#">Lorem ipsum dolor.</a></li>
    <li><a href="#">Lorem ipsum dolor.</a></li>
    <li><a href="#">Lorem ipsum dolor.</a></li>
    <li><a href="#">Lorem ipsum dolor.</a></li>
    <li><a href="#">Lorem ipsum dolor.</a></li>
</ul>
```
#### 第二种：强制内联

```
<style type="text/css">
.centerlist_inline{text-align: center;}
.centerlist_inline li{display: inline;}
</style>
<ul class="centerlist_inline">
<li><a href="">lorem1</a></li>
<li><a href="">lorem1</a></li>
<li><a href="">lorem1</a></li>
<li><a href="">lorem1</a></li>
</ul>
```
> 局限：块级元素改为内联元素，那么高度、宽度、margin-top,margin-bottom, padding-top,padding-bottom,等都不能用。

#### 第三种： 使用inline-block
> 如果大家用过用inline-block替换float可能就会清楚这个属性的好处了。

```
<style type="text/css">
.centerlist_inline-block{text-align: center; font-size:0; -letter-spacing:-1px;}
.centerlist_inline-block li{display: inline-block; *display: inline; *zoom:1; font-size:12px; letter-spacing:normal; word-spacing:normal;}
</style>
<ul>
<li><a href="">lorem1</a></li>
<li><a href="">lorem1</a></li>
<li><a href="">lorem1</a></li>
<li><a href="">lorem1</a></li>
</ul>
```
> 局限：有时我们在水平排列一组元素时, 高度不一致时,他们的位置 上下不能对齐 外层 需要定义一个 固定的高度
> 我一般处理,相等大小图片排列时,使用该方法 , 很好用, 兼容也不错, 8+

#### 第四种：table-cell
```
<style type="text/css">
.centerlist_table-cell{display:table; margin:0 auto;}
.centerlist_table-cell{display:table-cell;}
</style>
<ul class="centerlist_table-cell">
<li><a href="">lorem1</a></li>
<li><a href="">lorem1</a></li>
<li><a href="">lorem1</a></li>
<li><a href="">lorem1</a></li>
</ul>
```
> 缺点是不兼容ie6，ie7
> 推荐使用inline-block这种水平居中的方法，既保留了块级元素特性，而且完美兼容。就是代码有点多。另外你还可以使用表格的方式来水平居中。

说完了水平居中，下面说垂直居中。

如果元素是内联元素，并且只有一行，则我们可以通过line-height来设置与其高度同样大小，则实现了垂直居中了。

如果未知元素高度，则可以使用下面代码：
#### 第一种：display:table的方法

#### HTML 代码

```
<div class="middle-box">
    <div class="middle-inner">
        <p><span class="suc-tip">前端开发博客，专注前端开发和web教程</span><br/><span class="suc-link">快捷入口：<a href="http://caibaojian.com">http://caibaojian.com</a></span></p>
        <p style="display:none;"><span class="suc-tip">5年的老博客，一直致力于WEB开发</span></p>
    </div>
</div>
```
#### CSS 代码
```
.middle-box{display: table; height: 300px;}
.middle-inner{display: table-cell; vertical-align:middle; text-align:center;}
```

缺点就是不兼容ie6、ie7.怎么兼容呢？

当然是用另外一种相对定位和绝对定位的方式。

```
<!--[if lt IE 8]>
<style>
.middle-inner { position: absolute; top:50%;}
.middle-inner p {position: relative; top: -50%}
</style>
<![endif]-->
````
可以使用IE的特有的条件语法,也可以用ie hack来写.下面这个的代码实现了水平垂直多行代码（支持一行）居中对齐。目前测试IE、chrome和Firefox均兼容。代码如下：

```
.middle-box{display: table; height: 300px; border:1px solid #ff0000; width:400px; margin:0 auto; position:relative;}
.middle-inner{display: table-cell; vertical-align:middle; *position:absolute; *top:50%; *left:50%; width:100%; text-align:center;}
.middle-inner p{position:relative; *top:-50%; *left:-50%;}
```
以后遇到居中问题，这三句CSS就够用了。更多的css3 flexbox、margin负值等兼容性还需要探讨。
[演示](http://caibaojian.com/d/uploads/2015/09/middle-box.html)

#### 第二种方法：增加一个空白标签

#### HTML代码：
```
<div class="middle-box">
<p><span class="suc-tip">前端开发博客，专注前端开发和web教程</span><br/><span class="suc-link">快捷入口：<a href="http://caibaojian.com">http://caibaojian.com</a></span></p>
<i class="visible"></i>
<p style="display:none;"><span class="suc-tip">5年的老博客，一直致力于WEB开发</span></p>
</div>
```
#### CSS代码
```
.middle-box{height:300px; border: 1px solid #f00; width: 400px; margin: 0 auto; text-align: center; }
.middle-box p{vertical-align: middle; display: inline-block; *display: inline; *zoom: 1;}
.visible{height: 100%; vertical-align: middle; width: 0; display: inline-block;}
```
[演示](http://caibaojian.com/d/uploads/2015/09/vertical-middle.html)

> 著作权归作者所有。
> 商业转载请联系作者获得授权,非商业转载请注明出处。
> 链接: [http://caibaojian.com/370.html](http://caibaojian.com/370.html)
> 来源: [http://caibaojian.com](http://caibaojian.com)
> 如有侵权,请联系删除.


