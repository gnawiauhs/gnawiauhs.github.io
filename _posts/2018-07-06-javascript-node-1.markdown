---
layout:     post
title:      "JavaScript高级篇（一）"
subtitle:   "面向对象、原型、继承"
date:       2018-07-06 13:46:00
author:     "Vinst"
header-img: "img/post-head/html5-node.jpg"
catalog:    true
tags:
    - JavaScript
    - 学习笔记
---
## 1、面向对象

### 1.1 什么是面向对象程序设计
为了了解 **面向对象** 与 **面向过程** 的区别，我们先看案例1。

案例1：一辆汽车以60km/h，在一条长度1200km的公路上行驶，求其行驶完全程需要的时间。

```js
/* 面向过程 */
var time = 1200 / 60; // 计算汽车行驶时间
console.log(time); // 打印结果
```
```js
/* 面向对象 */
// 创建公路对象
var road = {
    long: 1200 // 公路长度
};

// 创建小汽车对象
var car = {
    speed: 60, // 汽车速度
    road: road, // 汽车在公路上行驶，与公路对象关联（road已声明）
    run: function(){ // 汽车行驶的方法，返回行驶速度
        return this.road.long / this.speed;
    }
}

var r = car.run(); // 执行汽车行驶的方法，返回行驶速度
console.log(r); // 打印结果（30）
```
虽然看上去面向对象比面向过程要复杂了很多，但是如果考虑到以后可能会改变某个变量（公路长度或汽车行驶速度），面向过程需要修改运算过程中的值，而面向对象只需要在执行运算方法之前通过`car.speed = 40`修改 **car** 对象的 **speed** 属性即可，可以有效避免修改错误和修改多处。

当程序复杂程度到达一定的量级，面向对象可以提高程序的可维护性。

如果后面我们的需求改变了，依旧需要汽车对象，但是要返回汽车的颜色。  
如果是面向过程开发，我们需要删除掉面向过程的所有代码，重新写代码返回汽车的颜色。而面向对象则不需要删除原来定义的对象，只需要给 **car** 对象增加一个 **color** 属性，扩展 **car** 对象。

**所以，面向对象程序设计的优势有：**
1. 提高代码的**可维护性**  
2. 提高代码的**可扩展性**

---

### 1.2 面向对象的方式操作DOM

HTML
```html
<div>111</div>
<div>222</div>
<div>333</div>
<div>444</div>
```

JS
```javascript
// 给div添加背景颜色
// 面向过程
var divs = document.getElementsByTagName('div');
for (var i=0; i<divs.length; i++) {
    divs[i].style.backgroundColor = 'red';
}

// 面向对象
var domOpr = {
    getDiv: function(){
        var divs = document.getElementsByTagName('div');
        return divs;
    },
    setStyle: function(){
        var divs = this.getDiv()
        for (var i=0; i<divs.length; i++) {
            divs[i].style.backgroundColor = 'red';
        }
    }
}
domOpr.setStyle();

```

如果多处需要相同的功能，面向对象的方法可以提高代码的**复用性**。

---

## 2、继承
传统的面向对象语言，继承是 **类** 与 **类** 之间的关系。而JS中，由于没有 **类** 的概念。所以是 **对象** 与 **对象** 之间的关系。

定义：在JS中，继承就是指使一个对象有权去访问另一个对象的能力。
比如：对象A能继承对象B的成员（属性和方法），那么，对象A就继承于对象B。

### 2.1 原型继承

#### 原型 
定义：原型就是指构造函数的prototype属性所引用的对象。
目的：解决同类对象数据共享问题。

示例：
```js
// 创建构造函数 Person
function Person(name, age){ 
    this.name = name;
    this.age = age;
    this.say = function(){
        console.log('hello!')
    }
} 
// 创建 Person 的实例对象
var p1 = new Person('张三', 19);
var p2 = new Person('李四', 20);
// Person.prototype 就是对象 p1 的原型
// p1.__proto__ 也是 p1 的原型
console.log(Person.prototype === p1.__proto__); // true
```
此时，p1和p2都有继承了构造函数 Person 的 say 属性，在控制台打印查看：
```js
p1.say(); // hello!
p2.say(); // hello!
```
这是 **构造函数继承**，那么 p1 的 say 和 p2 的 say 是不是同一个方法呢？

```js
// 打印查看
console.log(p1.say === p2.say); // false
```
查看结果发现两个 say 方法并不是同一个，所以在创建实例对象的时候开辟了两块内存分别存放了 p1.say 和 p2.say，这就导致了内存的浪费，所以我们需要通过原型共享数据来解决这个问题。
```js
// 创建构造函数 Person
function Person(name, age){ 
    this.name = name;
    this.age = age;
} 
// 创建 Person 的实例对象
var p1 = new Person('张三', 19);
var p2 = new Person('李四', 20);
// Person.prototype 就是对象 p1 的原型
// p1.__proto__ 也是 p1 的原型
// 在原型上创建一个 say 属性
Person.prototype.say = function(){
    console.log('hello!');
}
// 运行 p1.say 和 p2.say，并对比是否为同一个方法。
p1.say(); // hello!
p2.say(); // hello!
console.log(p1.say === p2.say); // true
```
如此便通过原型继承实现了数据共享。

> 构造函数中可以显式的指定return语句，但是如果返回的数据类型为简单数据类型，或者null undefined值都会被忽略，依旧返回的是构造函数的实例对象

### 2.2 类式继承
类式继承通过`call(this, ... , ...)`或`apply(this, arguments)`方法改变`this`指向实现继承。
```js
// 创建 Person 构造函数
function Person(name, age) {
    this.name = name;
    this.age = age;
}
// 创建 Student 构造函数
function Student(name, age, id){
    this.name = name;
    this.age = age;
    this.id = id;
}
```
`Student`对象是 `Person` 对象的一个分支，可以继承`Person`的属性。  
所以`Student` 属性可以这样写：
```js
function Student(name, age, id){
    Person.call(this, name, age);
    this.id = id;
}

var s = new Student('张三','20','123456789');
console.log(s); // {name: "张三", age: "20", id: "123456789"}
```
或者
```js
function Student(name, age, id){
    Person.apply(this, arguments); // arguments 是一个数组 也可以写成 [name, age]
    this.id = id;
}

var s = new Student('张三','20','123456789');
console.log(s); // {name: "张三", age: "20", id: "123456789"}
```

### 2.3 组合继承

通过前面对 **原型继承** 和 **类式继承** 的了解，我们发现 **原型继承** 用于继承静态数据， **类式继承** 用于继承动态参数，所以我们有时候需要同时使用 **原型继承** 和 **类式继承**，也就是 **组合继承**。
```js
function Person(name, age) {
    this.name = name;
    this.age = age;
}
// 类式继承
function Student(name, age, id){
    Person.call(this, name, age);
    this.id = id;
}
// 原型继承
Student.prototype.class = function(){
    console.log('English');
}
var s = new Student('张三', 20, '123456');
s.class();
```

### 2.4 extend方法

```js
var a = {
    name: 'g'
};

var b = {
    print: function() {
        console.log('Hello, js.')
    }
}
// 将 parent 对象上的成员赋值给 child
function extend(child, parent) {
    for (var pro in parent) {
        // child[pro] = parent[pro];
        // 缺点：会将parent对象的原型上的成员一同复制过来，所以需要先判断属性是否为parent私有的
        if (parent.hasOwnProperty(pro)){
            child[pro] = parent[pro];
        }
    }
}
extend(a,b);
a.print();
```