---
title:  Typora图片自动上传到图床
date: {{ date }}
author: 小枫
avatar: https://cdn.jsdelivr.net/gh/fengjing95/cdn@1.2/img/custom/avatar.jpg
authorLink: 
authorAbout: 一个好奇的人
authorDesc: 一个好奇的人
categories: 技术
comments: true
tags: 工具
keywords: 图床
description: Typora+picGo+gitee
photos: https://gitee.com/liuhao1108/picGoCDN/raw/master/img/typora-icon.png
---
# Typora图片自动上传到图床

你是否还在为找不到可靠的图床而烦恼

是否害怕图床网站关闭资源丢失

是否担心资源不能管理而发愁

**今天他来了**

## 1 下载安装picGo

地址在[这里](https://github.com/Molunerfinn/PicGo/releases)，根据需要的版本进行下载

![image-20200715191952303](https://gitee.com/liuhao1108/picGoCDN/raw/master/img/image-20200715191952303.png)

下载完成后进行安装

安装完之后在桌面右下角图标打开picGo详细界面

![image-20200715192408100](https://gitee.com/liuhao1108/picGoCDN/raw/master/img/image-20200715192408100.png)

## 2 配置picGo图床+gitee

picGo支持多个图床

![image-20200715193844116](https://gitee.com/liuhao1108/picGoCDN/raw/master/img/image-20200715193844116.png)

这里主要说一下gitee
新建一个**公开的仓库**，私有的在相册和Typora无法显示

搜索插件gitee（**需要安装Node环境**）

![image-20200715194024555](https://gitee.com/liuhao1108/picGoCDN/raw/master/img/image-20200715194024555.png)

据说是两个都可以，我只试过了gitee，安装好之后在上面的图床列表里就会出现gitee图床

![image-20200715194130651](https://gitee.com/liuhao1108/picGoCDN/raw/master/img/image-20200715194130651.png)

这里是配置信息

> owner：gitee用户名
>
> repo：gitee仓库名
>
> path：路径，存放到根目录可以不用写
>
> token：gitee个人令牌
>
> message：可以不写

关于gitee个人令牌的获取

点开gitee的设置，在左侧栏找到私人令牌，然后点击生成新令牌

![image-20200715194445782](https://gitee.com/liuhao1108/picGoCDN/raw/master/img/image-20200715194445782.png)

描述可以随便写一下，然后点击确认会生成一个token

![image-20200715194606276](https://gitee.com/liuhao1108/picGoCDN/raw/master/img/image-20200715194606276.png)

将token复制到picGo中就可以了

## 3 配置Typora+picGo

在Typora的偏好设置中将插入图片改为上传图片，上传服务修改为picGo App，并选择到安装目录

![image-20200715193003780](https://gitee.com/liuhao1108/picGoCDN/raw/master/img/image-20200715193003780.png)

点击验证

![image-20200715193212970](https://gitee.com/liuhao1108/picGoCDN/raw/master/img/image-20200715193212970.png)

如果出现false情况，看一下连接中的端口号，然后到picGo的设置中找到Server服务

![image-20200715193456911](https://gitee.com/liuhao1108/picGoCDN/raw/master/img/image-20200715193456911.png)

将端口号修改一致

然后保存，再试一下验证