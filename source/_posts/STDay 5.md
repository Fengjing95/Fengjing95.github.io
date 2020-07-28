---
title:  思途实训day5
date: {{ date }}
author: 小枫
avatar: https://cdn.jsdelivr.net/gh/fengjing95/cdn@1.2/img/custom/avatar.jpg
authorLink: 
authorAbout: 前端小白
authorDesc: 前端小白
categories: 生活
comments: true
tags: 思途实训
keywords: js，jQuery
description: 中享思途实训第五天
photos: https://gitee.com/liuhao1108/picGoCDN/raw/master/img/image-20200722153529693.png
---
# Day 5

引入js尽量放在body标签的最后，先加载静态标签，再加载js脚本

> jQuery表达式必须有分号

## jQuery

### 改变元素样式

```js
(() => {
	$('div').css({'color': 'red'});
})()
```

### click事件

```js
$(function () {
	$('button').click(() => {
		$('div').css({'color': 'red'});
	});
});
```

#### 导航栏颜色修改

![siblings](https://gitee.com/liuhao1108/picGoCDN/raw/master/img/siblings.gif)

```html
<ul id="nav-ul" onclick="navHandle()">
	<li id="li1">首页</li>
	<li id="li2">所有宝贝</li>
	<li id="li3">每周一上新</li>
	<li id="li4">生活馆</li>
	<li id="li5">特惠</li>
	<li id="li6">礼品区</li>
</ul>
```

```js
function navHandle() {
	var nodeId = window.event.target.id;
	// console.log(node);
	$('#' + nodeId).css({
		'color': '#d62cc0'
	}).siblings().css({
		'color': '#ffffff'
	});
}
```

> siblings()方法返回被选中元素的同级元素

### 鼠标经过和移出

```js
$(function() {
	$('#mouse').mouseenter(() => {
		$('#mouse').css({
			'background': 'red'
		});
	});
});
$(function() {
	$('#mouse').mouseleave(() => {
		$('#mouse').css({
			'background': '#409eff'
		});
	});
});
```

#### 淡入淡出效果

```js
$(function() {
	$('.b-f-1').mouseenter(() => {
		$('#black1').fadeOut(500);
	});
});
$(function() {
	$('.b-f-1').mouseleave(() => {
		$('#black1').fadeIn(300);
	});
});
```

![fadein](https://gitee.com/liuhao1108/picGoCDN/raw/master/img/fadein.gif)

#### 滑动效果

slideDown、slideUp

```js
$(function() {
	$('div').mouseenter(() => {
		$('div').slideDown(1000);
	});
});
$(function() {
	$('div').mouseleave(() => {
		$('div').slideUp(1000);
	});
});
```

## 总结

今天大概复习了一下jQuery，很多东西都忘了，需要再看一下