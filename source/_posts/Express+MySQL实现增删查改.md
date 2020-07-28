---
title:  Express+MySQL实现增删查改
date: {{ date }}
author: 小枫
avatar: https://cdn.jsdelivr.net/gh/fengjing95/cdn@1.2/img/custom/avatar.jpg
authorLink: 
authorAbout: 前端小白
authorDesc: 前端小白
categories: 技术
comments: true
tags: express
keywords: Express, MySQL
description: node后端使用mysql进行持久化
photos: https://gitee.com/liuhao1108/picGoCDN/raw/master/img/image-20200728215938329.png
---
# Express+MySQL实现增删查改

现在Node后台开发在网上找到的资料基本都是用的`MongoDB`数据库，不太容易找到使用`MySQL`数据库的资料，所以我整理了一下这篇文章，将会讲解如何使用Express和MySQL来实现CRUD

## 环境搭建

### 生成器

可以直接使用Express生成器自动生成Express工程

```shell
$ npm install -g express-generator
$ express --view=ejs myapp
```

### 手动搭建

#### 创建一个项目目录

```shell
$ npm init
```

+ 新建app.js入口文件
+ 新建router.js路由文件
+ 创建views文件夹，存放EJS模板文件（student.ejs, editStu.ejs）
+ 新建public公共资源

> views文件夹命名不可以是别的，会报错

#### 安装第三方模块

```shell
$ npm install express --save
$ npm install mysql --save
$ npm install ejs --save
```

## 编写代码

### 编写入口文件

实例化、模板引擎设置、静态资源、监听

```js
const express = require('express');
const app = express();
const stuRoute = require('/router')


// 设置模板引擎
app.set("view engine", "ejs");
// 加载静态资源
app.use(express.static('public'));

// 使用路由
app.use(stuRoute);

// 监听
app.listen(3001, () => {
    console.log('启动成功');
})
```



### 编写路由文件

```js
const express = require('express');
const route = express.Router();
const mysql = require('mysql');

// 配置数据库,连接池模式
var pool = mysql.createPool({
    connectionLimit: 10,    // 连接数量
    host: 'localhost',      // 地址
    user: 'liuhao',         // 数据库用户名
    password: '123456',     // 数据可密码
    database: 'ssmbuild'    // 数据库名
});

route.get('/student', (req, res) => {
    console.log("/student:", req.query);
    const sql = 'select * from books where bookName = ?';
    let params = ['java'];

    // 根据条件查询信息
    pool.getConnection(function (err, connection) {
        if (err) throw err; // not connected!

        connection.query(sql, params, function (error, results, fields) {

            connection.release();
            console.log(results);
            // 将数据传到ejs渲染
            res.render('student', {
                res: []
            })

            if (error) throw error;

        });
    });
})

module.exports = route;
```

## 效果展示

查询结果

![image-20200728215254516](https://gitee.com/liuhao1108/picGoCDN/raw/master/img/image-20200728215254516.png)

数据库数据

![image-20200728215339408](https://gitee.com/liuhao1108/picGoCDN/raw/master/img/image-20200728215339408.png)

这里可以看到数据已经查询成功



本篇主要讲解mysql模块使用，对数据渲染不再赘述
另外修改删除修改一下sql语句和params参数即可，开发时数据库部分一般会单独作为一个模块

现阶段来说一般是返回json数据，后期会再进行记录