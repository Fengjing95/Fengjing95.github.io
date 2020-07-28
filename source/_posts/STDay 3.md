---
title:  思途实训day3
date: {{ date }}
author: 小枫
avatar: https://cdn.jsdelivr.net/gh/fengjing95/cdn@1.2/img/custom/avatar.jpg
authorLink: 
authorAbout: 前端小白
authorDesc: 前端小白
categories: 生活
comments: true
tags: 思途实训
keywords: HTML, css
description: 中享思途实训第三天
photos: https://gitee.com/liuhao1108/picGoCDN/raw/master/img/image-20200722153529693.png
---
# Day 3

## HTML标签。。。

从0开始的那种。。。

## css样式

### 通配符选择器

```css
* {
	margin: 0;
	list-style: none; /* 去掉list圆点 */
	text-decoration: none; /* 去掉下划线 */
}
```

### 列表右浮动只给父级不给子级

### 背景图片

引入背景图片必须设置高度，否则不显示

```css
.binner {
    /* no-repeat不平铺 */
	background: url(../img/TB183NQapLM8KJjSZFBSutJHVXa.jpg) no-repeat;
	height: 568px;
    background-size: 100% auto; /* 图片自适应 */
}
```

### 行高等于div高度时自动居中

```css
.nav-f {
	width: 660px;
	height: 120px;
	position: absolute;
	left: 168px;
	line-height: 120px;
}
```

### 精灵图

使用Photoshop信息面板配合精灵图设置图片

![image-20200723153304428](https://gitee.com/liuhao1108/picGoCDN/raw/master/img/image-20200723153304428.png)

比如这张精灵图

```css
 .shopping {
	width: 30px;
	height: 30px;
	background: url(../img/icon.png);
	background-position: -16px -133px;
}
```

![image-20200723153626720](https://gitee.com/liuhao1108/picGoCDN/raw/master/img/image-20200723153626720.png)

引入图片之后将鼠标移至图标左上角，看到位置是`X：16，Y：133`，将图片位置设置为`-16px,-133px`，将图片沿着X轴Y轴移动之后，浏览器会自动根据设置的宽高从起点位置裁切

