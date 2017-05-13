---
title: CSS编码规范
tags:
  - CSS
categories: CSS
date: 2017-05-12 11:20:21
---

## 1.前言
制作规范的主要目的在于：
+ 培养自己良好的编码和协同习惯
+ 统一代码风格，提升代码质量和可维护性
+ 减少无谓的思考，提升工作效率

## 2.代码风格

### 2.1 文件
[建议] css文件使用无 BOM 的 UTF-8 编码。
解释：UTF-8 编码具有更广泛的适应性。BOM 在使用程序或工具处理文件时可能造成不必要的干扰。
参考：[「带 BOM 的 UTF-8」和「无 BOM 的 UTF-8」有什么区别](https://www.zhihu.com/question/20167122)

### 2.2 @charset
[建议] 为每个css文档显示的定义编码，在文档首行定义 @charset "utf-8"。
示例：
``` code
@charset "utf-8";

html {
    margin: 0;
    padding: 0;
}
```

### 2.3 @import
[建议] 尽量不要使用@import导入css

### 2.4 缩进
[强制] 使用 4 个空格做为一个缩进层级，不允许使用 2 个空格 或 tab 字符。
示例：
``` code
.item {
    margin: 0;
    padding: 0;
}
```

### 2.5 换行
[强制] 规则之间使用一个换行符分开。
示例：
``` code
html {
    margin: 0;
    padding: 0;
}

body {
    margin: 0;
    padding: 0;
}
```
[强制] 书写选择器之前不能带空格，选择器 与第一个 { 必须在同一行， } 结尾必须另起一行。
``` code
/* good */
.item {
    margin: 0;
    padding: 0;
}

/* bad */
.item
{
    margin: 0;
    padding: 0;
}

  .item {
    margin: 0;
    padding: 0;
}

.item {
    margin: 0;}
```

### 2.6 空格
[强制] 选择器 与 { 之间必须包含一个空格。
``` code
/* good */
html {
    margin: 0;
    padding: 0;
}

/* bad */
html    {
    margin: 0;
    padding: 0;
}
```
[强制] 属性名 与之后的 : 之间不允许包含空格， : 与 属性值 之间必须包含空格。
``` code
/* good */
html {
    margin: 0;
    padding: 0;
}

/* bad */
html {
    margin : 0;
    padding : 0;
}
```
[强制] 列表型属性值 书写在单行时，, 后必须跟一个空格。
``` code
/* good */
.item {
    font-family: Arial, sans-serif;
    background-color: rgba(0, 0, 0, .2);
}

/* bad */
.item {
    font-family: Arial,sans-serif;
    background-color: rgba(0,0,0,.2);
}
```

### 2.7 行长度
[强制] 每行不得超过 120 个字符，除非单行不可分割。
解释：
常见不可分割的场景为URL超长。

[建议] 对于超长的样式，在样式值的 空格 处或 , 后换行，建议按逻辑分组。
示例：
``` code
/* 不同属性值按逻辑分组 */
.item {
    background:
        transparent url(aVeryVeryVeryLongUrlIsPlacedHere)
        no-repeat 0 0;
}

/* 可重复多次的属性，每次重复一行 */
.item {
    background-image:
        url(aVeryVeryVeryLongUrlIsPlacedHere)
        url(anotherVeryVeryVeryLongUrlIsPlacedHere);
}

/* 类似函数的属性值可以根据函数调用的缩进进行 */
.item {
    background-image: -webkit-gradient(
        linear,
        left bottom,
        left top,
        color-stop(0.04, rgb(88,94,124)),
        color-stop(0.52, rgb(115,123,162))
    );
}
```

### 2.8 选择器
[强制] 当一个 rule 包含多个 selector 时，每个选择器声明必须独占一行。
``` code
/* good */
.post,
.page,
.comment {
    line-height: 1.5;
}

/* bad */
.post, .page, .comment {
    line-height: 1.5;
}
```

[强制] >、+、~ 选择器的两边各保留一个空格。
``` code
/* good */
main > nav {
    padding: 10px;
}

label + input {
    margin-left: 5px;
}

input:checked ~ button {
    background-color: #69c;
}

/* bad */
main>nav {
    padding: 10px;
}

label+input {
    margin-left: 5px;
}

input:checked~button {
    background-color: #69c;
}
```

[强制] 属性选择器中的值必须用双引号包围。
解释：
不允许使用单引号，不允许不使用引号。
``` code
/* good */
article[character="juliet"] {
    voice-family: "Vivien Leigh", victoria, female
}

/* bad */
article[character='juliet'] {
    voice-family: "Vivien Leigh", victoria, female
}
```

## 2.9 属性
[强制] 属性定义必须另起一行。
``` code
/* good */
.selector {
    margin: 0;
    padding: 0;
}

/* bad */
.selector { margin: 0; padding: 0; }
```

## 2.10 命名
[建议] 用尽可能简短的，有助于理解的命名去传达ID或类的内容。
``` code
/* good */
#nav {
    background-color: #000;
}

.author {
    color: #fff;
}

/* bad */
#navigation {
    background-color: #000;
}

.atr {
    color: #fff;
}
```

[强制] 使用 - 符号作为选择器命名的分隔符。
``` code
/* good */
#video-id {
    padding: 10px;
}
.ads-sample {
    margin: 0;
}

/* bad */
.demoimage {
    display: block;
}
.error_status {
    margin: 0;
}
```

[建议] 选择器中避免使用标签名来命名。
``` code
/* good */
.item .item-head {
    background-color: #000;
}

/* bad */
.item .span {
    background-color: #000;
}
```

[建议] 选择器命名时可适当加入可理解的前缀，规则因尽可能简短。
解释：这样可以有利于防止命名冲突，并使维护变得容易。
``` code
/* good */
.btn-pause { /* Pause Button */
    background-color: #000;
}

.ali-user-list { /* Alibaba User list */
    margin: 0;
}

/* bad */
.pause {
    background-color: #000;
}

.user-list {
    margin: 0;
}
```

## 2.11 注释
[建议] 注释原则：在书写每个大的模块之间、结构之间或者特别需要注明的地方应当给与相应的注释。
``` code
/* 模块之间的注释，有助于在书写时寻找到相应模块的起始位置 */
/* Banner */
.m-banner {}
.m-banner .banner-head {}

/* Footer */
.m-footer {}
.m-footer .footer-head {}

/* 结构之间的注释有助于在大的模块里面，找到相应的结构代码 */
/* Banner */
.m-banner {
    margin: 0;
    padding: 0;
}
.m-banner .banner-head {
    /* Banner head */
    color: #555;
}
.m-banner .banner-head .icon-ship {
    background: url(ship.png) no-repeat 0 0;
}
.m-banner .banner-foot {
    /* Banner foot */
    color: #333;
}

/* 在特别需要注明的地方也需要有适当的注释 */
@media
    (-webkit-min-device-pixel-ratio: 2), /* Webkit-based browsers */
    (min-resolution: 2dppx),             /* The standard way */
    (min-resolution: 192dpi) {           /* dppx fallback */
    color: #555;
    width: 10px;
}
```
[建议] 注释与选择器之间不换行，尽量不要带有一些抢眼的特殊字符。
``` code
/* good */
/* Galary Header */
.glr-head {
    margin: 0;
}

/* bad */
/* ---------------Galary Header---------------------- */
.glr-head {
    margin: 0;
}

/* ##############Galary Header################# */
.glr-head {
    margin: 0;
}
```

## 3. 通用

### 3.1 选择器
[强制] 如无必要，不得为 id、class 选择器添加类型选择器进行限定。
解释：在性能和维护性上，都有一定的影响。
``` code
/* good */
#error,
.danger-message {
    font-color: #c00;
}

/* bad */
dialog#error,
p.danger-message {
    font-color: #c00;
}
```

[建议] 选择器的嵌套层级应不大于 3 级，位置靠后的限定条件应尽可能精确。
示例：
``` code
/* good */
#username input {}
.comment .avatar .icon {}

/* bad */
.page .header .login #username input {}
.comment div * {}
```

## 7. 说明
本规范基于一些大厂规范和作者觉得比较好的方式做的一个整理
命名方式 和 注释规范 还有部分内容待整理

## 8. 版本
当前版本 v1.0 beta
作者 Shynee shynefu@gmail.com
最后更新时间 2017-05-12