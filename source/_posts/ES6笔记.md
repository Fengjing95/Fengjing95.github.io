---
title:  Hello World
date: {{ date }}
author: 小枫
avatar: https://cdn.jsdelivr.net/gh/fengjing95/cdn@1.2/img/custom/avatar.jpg
authorLink: 
authorAbout: 前端小白
authorDesc: 前端小白
categories: 技术
comments: true
tags: js
keywords: js, ES
description: ECMAScript6学习笔记
photos: https://ae01.alicdn.com/kf/H5aff3b00be9642e5aafff775358bae53m.jpg
---
# ES6笔记

## 变量

### let和const

**var存在的问题**

1. 可以重复声明
2. 无法限制修改
3. 没有块级作用域

**ES6新的定义变量**

let

> 不能重复声明
>
> 变量，可以修改
>
> 块级作用域

const

> 不能重复声明
>
> 常量，不能修改
>
> 块级作用域

***<u>最大的区别：const一经定义值不能再变</u>***

## 函数

### 箭头函数

```js
let show = function(n1,n2) {
    return n1-n2;
}
----------等价--------------
let show = (n1, n2) => {
    return n1-n2;
}
```

如果只有一个参数，()可以省略

```js
let show = (n) => {
    return n;
}
--------省略--------
let show = n => {
    return n;
}
```

如果只有一个return，{}可以省略

```js
let show = n => {
    return 2*n;
}
-------省略--------
let show = n => 2*n;
```

>箭头函数的this不会变：this指向的是当前对象，传统的function需要定义一个const that= this才能在里面的函数访问到最外层的this，箭头函数不会改变this指向，也就是说，无需定义that就可以用this访问原来的对象

[箭头函数的优势和劣势](https://www.dazhuanlan.com/2019/09/28/5d8ecd7dd484e/)

### 参数

#### `...args`

**接收参数**

命名随意，但必须放到参数最后，用于收集剩余参数

```js
let show = function (a, b, ...args) {
	alert(a);
	alert(b);
	alert(args);
}
			
show(14,2,3,4,5);
```

多余的参数将会由args接收

![](C:\Users\刘浩\Desktop\笔记\图片\...args.png)

**展开数组**

展开后效果跟直接把数组放在那一样

```js
let arr = [1,2,3,4];
show(...arr);// == show(1,2,3,4)
-------------------
let arr1=[1,2,3];
let arr2=[4,5,6];
let arr=[...arr1,...arr2];
// == let arr=[1,2,3,4,5,6];
```

#### 默认参数

```js
let show = function (a, b=5, c=10) {
		XXX
}
show(12);
```

当传的参数只有一个的时候，b默认是5，c默认是10；

当传参数大于一位时，会依次顶替默认参数

## 解构赋值

**左右两边结构必须一样**

```js
let [a, b, c] = [1,2,3]
let {a,b,c} = {a:1,b:2,c:3}
```

**右边必须合法**

**声明和赋值不能分开**

```js
let [a, b] = [5, 12];// 合法
------------------------
let [a, b];
[a, b] = [5, 12];// 报错，解构赋值声明和赋值不能分开
```

## 数组

### map

映射————一个对一个

```js
let arr = [1, 2, 3, 4];
let result = arr.map(item => item * 2);
// result 2,4,6,8
```

### reduce

汇总————一堆出来一个

```js
let arr= [12, 8, 9, 16];
let result = arr.reduce( function (tmp, item, index) {
    return tmp + item;
})
```

function中的三个参数分别是存储的和的中间数、要计算的数、索引

### filter

过滤器————保留一部分

```js
let arr = [10,3,16,15,21,20];
let result = arr.filter(item => {
	if(item % 3 == 0) {
		return true;
	}
	return false;
});
alert(result);
--------------------------------
// json类型
let arr = [
    {name: 'tom', price: 75},
    {name: 'jerry', price: 60}
];
let result = arr.filter(item => {
	return item.price>65;
});
console.log(result);
```

当filter中的方法返回true的时候数据保留，返回false数据删除

### forEach

循环（迭代）————每一项进行操作

吧数组中的每一项都放到方法中执行

## 字符串

### 两个新方法

**startsWith**

匹配前面的字符串，相同返回true，不相同返回false

**endWith**

匹配末尾的字符串，相同返回true，不相同返回false

应用：检测文件后缀

### 字符串模板

**字符串拼接**

```js
let a = 'AScri';
let str = `ECM${a}pt6`;
alert(str);
// str=ECMAScript6
```

<u>*注意：插入字符串的字符串要用反单引号（数字键盘1左边的那个）*</u>

应用，拼接字符串

```js
let html = `<div>
	<h1>${title}</h1>
	<p>${content}</p>
</div>`;
```

优势：直接把字符串插到字符串中；可以折行

## 面向对象

### 语法

```js
class User {
	constructor(name, age) {
		this.name = name;
		this.age = age;
	}
	showName() {
		alert(this.name);
	}
	showAge() {
		alert(this.age);
	}
}
var user = new User('Tom', 18);
user.showName();
user.showAge();
```

对象创建关键字class，相当于java的类

构造器关键字constructor，相当java的构造函数

方法直接写在class里面，不需要加function

### 继承

```js
class VipUser extends User {
	constructor(name, age, level) {
		super(name, age);
		this.level = level;
	}
				
	showLevel() {
		alert(this.level);
	}
}
			
var vip = new VipUser('Tom', 18, 3);
vip.showName();
vip.showAge();
vip.showLevel();
```

继承关键字extens，相当于java的继承

构造函数中使用super关键字，调用父类的构造函数

添加新的属性和新的方法

## JSON

### 标准写法

1. 只能用双引号

2. 所有名字都必须用引号括起来

   ```json
   {
       "a": "abx",
       "b": 12,
       "c": true
   }
   ```

### 格式化为字符串

```js
let json = {a: 11, b: 12};
alert(JSON.stringify(json));
```

JSON.stringify()得到的结果是一个**字符串**

### 格式化为JSON

```js
let str = '{"a": 11, "b": 12}';
console.log(JSON.parse(str));
```

JSON.parse()得到的结果是一个json对象，但是，**<u>字符串的内容必须符合json格式标准</u>**，另外，双引号的外面是单引号

### 简写

**属性名简写**

```js
let a = 12;
let b = 5;
let json = {a, b, c: 15};
console.log(json);
```

当已经存在的值和json属性名一样的时候，可以只写值，不一样的可以按照json格式添加

> 这里的json指的是json字面量

**方法简写**

```js
let json = {
	a: 12,
	show() {
		console.log(this.a);
	}
}
json.show();
```

方法可以只写方法名，省略 `function`

## Promise

作用：消除异步操作，用同步的方式来写异步代码

> 异步：操作之间没啥关系，同时进行多个操作；代码复杂
>
> 同步：同时只能做一件事，前面的事没干完后面的事不能开始；代码简单

**封装ajax（基于jquery）**

```js
let ajax = new Promise(function (resolve, reject) {
    $.ajax({
        url: 'js/arr.txt',
        dataType: 'json',
        success(json) {
            resolve(json);
        },
        error(err) {
            reject(err);
        }
    })
});
ajax.then(result => {
    alert(result);
}, err => {
    console.log(err);
})
```

### Promise.all()

当有两个Promise对象时，可以使用Promisr.all()处理两个Promise对象

```js
Promise.all([
    ajax1, ajax2
]).then(result => {
    let [arr1, arr2] = result;
    alert(arr1);
    alert(arr2);
}, err => {
    console.log(err);
})
```

**<u>这里注意</u>**，当使用.all处理多个Promise对象时，有一个出错就会报错，全部成功才会执行成功的回调函数

有多个ajax请求不同地址的时候可以，再次封装

```js
function createPromise(url) {
    return new Promise(function(resolve, reject) {
        $.ajax({
            url,
            dataType: 'json',
            success(json) {
                resolve(json);
            },
            error(err) {
                reject(err);
            }
        })
    });
}
Promise.all([
    createPromise('js/arr.txt'),
    createPromise('js/arr2.txt')
]).then(result => {
    let [arr1, arr2] = result;
    alert(arr1);
    alert(arr2);
}, err => {
    console.log(err);
})
```

> 以上只是示例，jquery的作者当然想到了这一点，$.ajax()是有返回值的（高版本，低版本可能没有）
>
> ```js
> let p = $.ajax({url: 'js/arr.txt', dataType: 'json'});
> ```
>
> 可以将 `$.ajax({url: 'js/arr.txt', dataType: 'json'})` 放到Promise.all()里面，代替上面的createPromise方法

### Promise.race()

同时处理多个Promise对象，有一个先完成的就停止

应用场景，同时向多个负载发送请求

### Promise链式调用

```js
let test = new Promise((resolve, reject) => {
    let random = Math.random()
    if (random > 0.5) {
        resolve('大于0.5')
    } else {
        reject('小于等于0.5')
    }
})

let p = test.then((result) => {
    console.log(result)
    return result
}).catch((result) => {
    console.log(result)
    return result
}).then((result) => {
    console.log(result)
    return result
}).then((result) => {
    console.log('last', result)
})

console.log(p)
-------------------------
Promise { <pending> }	// p
大于0.5	// 或者小于，下同
大于0.5
last 大于0.5
```

> + promise 的 then 方法里面可以继续返回一个新的 promise 对象
>
> + 下一个 then 方法的参数是上一个 promise 对象的 resolve 参数
>
> + catch 方法的参数是其之前某个 promise 对象的 rejecte 参数
>
> + 一旦某个 then 方法里面的 promise 状态改变为了 rejected，则promise 方法连会跳过后面的 then 直接执行 catch；如果状态一直为fulfilled，catch里面的的代码不执行
>
> + catch 方法里面依旧可以返回一个新的 promise 对象

 promies的三种状态是未决的pending（进行中），和已决的fulfilled（成功）/rejected（失败），reslove和reject是成功和失败的参数，在promies里调用参数之后then方法才会执行 

参考资料：

[深入理解Promise三种状态与链式调用](https://www.jianshu.com/p/dc61ea153874)

[Promise对象then方法链式调用](https://www.jianshu.com/p/8252056e5d9c)

## 生成器函数

### generator

> 普通函数：一直执行到最后
>
> generator函数：中间可以暂停

```js
function *show() {
    alert('1');
    yield;
    alert('2');
}
let obj = show();
obj.next();
obj.next();
```

直接运行show()并不会有任何反应，用show来创建一个对象，用next方法可以执行，遇到yield停下，再执行next可以继续运行之后的部分

原理是把一个大函数的代码切分成多个小函数，每next一次执行一次

一个生成器中可以存在多个yield；注意函数命名方式 `function *show(){}`，带有星号

### yield

**可以传参**

第一个next无法传参，可以理解为generator的启动器，第二个next开始向第一个yield传参

```js
function *show() {
    alert('1');
    let a = yield;
    alert(a);
}
let obj = show();
obj.next();
obj.next(10);
--------------------------
// 打印结果 a=10
```

**有返回值**

```js
function *show() {
    alert('1');
    let a = yield 'axc' + 'ac';
    alert(a); // 10
    // 如果这里return 55，那么下边b1的value就是55
}
let obj = show();
let a1 = obj.next();
console.log(a1);	// {value: "axcac", done: false}
let b1 = obj.next(10);
console.log(b1);	// {value: undifind, done: true}
```

一个yield相当于一个被分解成小函数的return

> 总结：第一个yield返回的值给了第一个next，第二个next的参数给了第一个yield

## 附：ES7 async await

```js
async function doSome() {
    try {
        let data1 = await function(data);
		let data2 = await function(data1);
		let data3 = await function(data2);
    } catch(err) {
        console.log("Error:" + err);
    }
}
```

用同步的方式实现异步

await的返回值是promise；await后面可以用Promise.all()执行多个Promise操作

> awat 外面必须包裹着async， 把await和成功后的操作放到try里，失败的放在catch 

参考资料： [async和await](https://www.jianshu.com/p/b4fd76c61dc9)