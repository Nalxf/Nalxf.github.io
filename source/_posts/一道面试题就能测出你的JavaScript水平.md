---
title: 一道面试题就能测出你的JavaScript水平
date: 2017-08-08 10:41:44
layout: post
categories:
- 随笔
tags:
- 心情
- 面试题
---

![Alt text](http://ou5ix7hfz.bkt.clouddn.com/20170808-1.png)

<!-- more -->

### 这是一道非常好的面试题， 考察以下知识点:

* this的指向
* 原型(prototype)以及原型链
* 继承
* 引用

### 要解出这道题，要理解以下几句话就可以了：

1. 每一个构造函数，都有一个原型[[prototype]]属性 指向构造函数的原型对象
2. 每一个实例生成的时候，都会在内存中产生一块新的堆内存
3. 每一实例都有一个隐式原型__proto__ 指向构造函数的原型对象
4. this的指向 取决于this调用时的位置, 在这道题中， 也可以简单理解为， 谁调用方法， this就指向哪个对象
5. 数组和字面量对象 都是 引用
6. 原型链的查找规则：  就近原则
> 当实例上存在属性时， 用实例上的
如果实例不存在，顺在原型链，往上查找，如果存在，就使用原型链的
如果原型链都不存在，就用Object原型对象上的
如果Object原型对象都不存在， 就是undefined

### 为了帮助大家， 我贴出课堂上的示意图， 如果有不理解的，欢迎互动，交流
![Alt text](http://ou5ix7hfz.bkt.clouddn.com/20170808-2.jpg)

![Alt text](http://ou5ix7hfz.bkt.clouddn.com/20170808-3.jpg)


#### 问题

<ul>
    <ol class="problem">第二次 child1.show()  打印的是 5 (5) [1, 2, 1, 11, 12] 5 ?    a = 5 从哪里来的</ol>
    <ol class="problem">第二次 child2.show()  打印的是 6 (5) [1, 2, 1, 11, 12] 5 ?    a = 6 是从哪里来的</ol>
</ul>


<hr>


{% blockquote [作者：ghostwu[, 源自]] [http://www.cnblogs.com/ghostwu/p/7272132.html] %}
文章著作权归作者所有，如有侵权，请联系删除.
{% endblockquote %}

<br />
















