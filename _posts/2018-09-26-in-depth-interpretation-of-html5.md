---
layout:     post
title:      "深入解读 HTML5"
subtitle:   "IN-DEPTH INTERPRETATION OF HTML5"
date:       2018-09-26 12:00:00
author:     "Vinst"
header-img: "img/post-head/html5-note.jpg"
catalog:    true
tags:

    - HTML5
    - 学习笔记
---

HTML5是HTML第五代语法标准，发布于2014年10月28日。虽然早已经不是什么新东西，但是平时真正用到项目中的 HTML5 特性并不是很多（可能是因为我做的产品大多数是PC端的，需要兼容IE低版本浏览器），所以今天抽空来重新熟悉一下 HTML5 到底为我们提供了哪些不一样的东西。

## 1、新标签

大家都知道 HTML5 摒弃旧版本的一些如：`<center>` `<font>` `<frame>` 等这类没有意义又容易出现问题的标签，保留却重定义一些标签，同时新增了一些如 `<header>` `<footer>` `<nav>` `<article>` 等这类语义化标签。

使用语义化标签的目的，是为了使网页结构更加清晰，方便阅读，同时也方便搜索引擎根据标签的语义确定上下文和权重。

HTML5 新增的标签大致如下：

### 1.1 删除了哪些标签

**纯表现的元素**

`besefont`、 `big`、`center`、 `font`、`s`、`strike`、`tt`、`u`

**对可用性产生负面影响的元素**

`frame`、`frameset`、`noframes`

**产生混肴的元素**

`acronym`、 `applet`、 `isindex`、`dir`

### 1.2 重定义了哪些标签

**显示不变，只是表达的含义进行了重新定义的标签**

| 标签                                                 | 备注                                                         |
| ---------------------------------------------------- | ------------------------------------------------------------ |
| [b](http://www.runoob.com/tags/tag-b.html)           | <b>代表内联文本，通常是粗体，没用传递表示重要的意思          |
| [i](http://www.runoob.com/tags/tag-i.html)           | <i>代表内联文本，通常是斜体，没有传递表达重要的意思          |
| [dd](http://www.runoob.com/tags/tag-dd.html)         | 可以同`detailsy`与`figure`一同使用，定义包含文本，`dialog`亦可使用 |
| [dt](http://www.runoob.com/tags/tag-dt.html)         | 可以同`details`与`figrue`一同使用，汇总细节，`dialog`也可用  |
| [hr](http://www.runoob.com/tags/tag-hr.html)         | 表示主题结束，而不是水平线，虽然显示相同                     |
| [menu](http://www.runoob.com/tags/tag-menu.html)     | 重新定义用户界面的菜单，配合`commond`或者`menuitem`使用      |
| [small](http://www.runoob.com/tags/tag-small.html)   | <small>表示小字体，例如打印注释或则法律条款                  |
| [strong](http://www.runoob.com/tags/tag-strong.html) | <strong>表示重要性而不是强调符号                             |

### 1.3 新增了哪些标签

#### 1.3.1 结构标签（块状元素）——有意义的div

| 标签                                                         | 备注                                 |
| ------------------------------------------------------------ | ------------------------------------ |
| [article](http://www.runoob.com/tags/tag-article.html)       | 标记定义一篇文章                     |
| [header](http://www.runoob.com/tags/tag-header.html)         | 标记定义一个页面或一个区域的头部     |
| [nav](http://www.runoob.com/tags/tag-nav.html)               | 标记定义导航链接                     |
| [section](http://www.runoob.com/tags/tag-section.html)       | 标记定义一个区域                     |
| [aisde](http://www.runoob.com/tags/tag-aisde.html)           | 标记定义页面内容的侧边栏             |
| [hgroup](http://www.runoob.com/tags/tag-hgroup.html)         | 标记定义文件中一个区块的相关信息     |
| [figure](http://www.runoob.com/tags/tag-figure.html)         | 标记定义一组媒体内容以及他们的标题   |
| [figcaption](http://www.runoob.com/tags/tag-figcaption.html) | 标记定义figure元素的标题             |
| [footer](http://www.runoob.com/tags/tag-footer.html)         | 标记定义一个页面或一个区域的底部     |
| [dialog](http://www.runoob.com/tags/tag-dialog.html)         | 标记定义一个对话框（会话框）类似微信 |

#### 1.3.2 多媒体标签

| 标签                                                 | 备注                                        |
| ---------------------------------------------------- | ------------------------------------------- |
| [video](http://www.runoob.com/tags/tag-video.html)   | 标记定义一个视屏                            |
| [audio](http://www.runoob.com/tags/tag-audio.html)   | 标记定义音频内容                            |
| [source](http://www.runoob.com/tags/tag-source.html) | 标记定义媒体资源                            |
| [canvas](http://www.runoob.com/tags/tag-canvas.html) | 标记定义图片                                |
| [embed](http://www.runoob.com/tags/tag-embed.html)   | 标记定义外部的可交互的内容或插件，比如flash |

> 标签的意义：多媒体标签的出现意味着多媒体的发展以及支持不适用插件的情况下即可操作媒体文件，极大提升了用户体验。

关于多媒体标签的应用，笔者会另外发布相关文章，在此不过多展开。

#### 1.3.3 Web应用标签

**状态标签**

| 标签                                                     | 备注                                                         |
| -------------------------------------------------------- | ------------------------------------------------------------ |
| [meter](http://www.runoob.com/tags/tag-meter.html)       | 实时状态显示：气压、气温。 例：<meter value="0.3"></meter>30% |
| [progress](http://www.runoob.com/tags/tag-progress.html) | 任务过程：安装、 加载。    例：<progress></progress>         |

**列表标签**

| 标签                                                     | 备注                                                         |
| -------------------------------------------------------- | ------------------------------------------------------------ |
| [datalist](http://www.runoob.com/tags/tag-datalist.html) | 为input标记定义一个下拉列表，配合option                      |
| [details](http://www.runoob.com/tags/tag-details.html)   | 标记定义一个元素的详细内容，配合summary                      |
| [summary](http://www.runoob.com/tags/tag-summary.html)   | 标签为`<details>` 元素定义一个可见的标题。当用户点击标题时会显示出详细信息。 |

**Menu**

| 标签                                                     | 备注                                      |
| -------------------------------------------------------- | ----------------------------------------- |
| [menu](http://www.runoob.com/tags/tag-menu.html)         | 命令列表（目前所有的主流浏览器都不支持）  |
| [menuitem](http://www.runoob.com/tags/tag-menuitem.html) | menu命令列表的标签（只有FireFox9.0+支持） |
| [command](http://www.runoob.com/tags/tag-command.html)   | menu标记定义一个命令按钮（只有IE9支持）   |

#### 1.3.4 其他标签

**注释标签**

| 标签                                             | 备注                                       |
| ------------------------------------------------ | ------------------------------------------ |
| [ruby](http://www.runoob.com/tags/tag-ruby.html) | 标记定义注释或音标                         |
| [rp](http://www.runoob.com/tags/tag-rp.html)     | 告诉那些不支持ruby的元素的浏览器如何去显示 |
| [et](http://www.runoob.com/tags/tag-et.html)     | 标记定义对rubyd 注释内容文本               |

**其他标签**

| 标签                                                 | 备注                                                |
| ---------------------------------------------------- | --------------------------------------------------- |
| [mark](http://www.runoob.com/tags/tag-mark.html)     | 标记定义有标记的文本（黄色选中状态）                |
| [output](http://www.runoob.com/tags/tag-output.html) | 标记定义一些输出类型，计算表单结果配合oninput事件   |
| [keygen](http://www.runoob.com/tags/tag-keygen.html) | 标记定义表单里生成的键值（加密信息传送）            |
| [time](http://www.runoob.com/tags/tag-time.html)     | 标记定义一个日期/时间，目前所有主流的浏览器都不支持 |

### 1.5 语义化标签兼容性

对于不支持HTML5语法的浏览器（如：IE8及以下版本浏览器），要想使用这些新标签，需要那个通过JavaScript创建该标签。具体做法如下（以`<header>`标签为例）：
1. 在CSS中设置标签样式为块级
```
header { display: block; }
```
2. 通过JavaScript的DOM方式创建该标签
```
document.createElement('header');
```

由于HTML5新增的标签很多， 如果用上述方法创建标签也比较麻烦，所以我们可以通过简单引用[html5shiv.js](https://github.com/aFarkas/html5shiv)文件解决这个问题。

***

## 2、新功能

### 2.1 表单元素

自带格式验证

| 类型                    | 备注 |
| ----------------------- | ---- |
| `<input type="email">`  | 邮箱 |
| `<input type="number">` | 数字 |
| `<input type="url">`    | 地址 |
| `<input type="range">`  | 滑块 |
| `<input type="color">`  | 颜色 |
| `<input type="time">`   | 时间 |
| ......                  |      |

```html
<form autocomplete="on" novalidate></form>
<!--
autocomplete: on表示开启智能提示；off表示关闭智能提示
novalidate: 关闭智能验证
-->
```

```html
<form action="" method="get" id="fm">
  <input type="text" value="" autofocus placeholder="请输入名字" required>
  <input type="submit" value="提交">
</form>
<input type="text" name="name" form="fm">
<!--
autofocus: 自动获取焦点
placeholder: 文本框提示信息
required: 该属性出现，当前的表单元素必须有验证
form: 该属性出现在表单标签中，值设置为form标签的ID值，该标签可以提交
-->
```

```html
<input type="text" value="" list="url_list">
<datalist id="url_list">
    <option value="https://www.baidu.com">百度</option>
    <option value="https://www.google.com">谷歌</option>
    <option value="https://www.youku.com">优酷</option>
    <option value="https://www.qq.com">腾讯</option>
</datalist>
```

### 2.2 DOM扩展

#### 2.2.1 获取元素

原来我们获取元素的方法是：

```js
// 通过id获取元素
document.getElementById("id");
// 通过class获取元素
document.getElementsByClassName("class");
// 通过标签名获取元素
document.getElementByTagName("target");
```

或者使用 jQuery 的 `$("选择器")`。

HTML5为我们带来了新方法：

```js
// 获取第一个与选择器匹配的元素
document.querySelector("选择器");
// 获取所有与选择器匹配的元素，返回一个数组
document.querySelectorAll("选择器");
```

#### 2.2.2 自定义属性

```html
<div id="dv" data-name="名字" data-age="20" data-user-sex="男"></div>
```
HTML5通过 "data-属性名" 的方式创建自定义属性。

JavaScript 通过`dataset`对象获取自定义属性。
> 注：获取dataset中的属性名需要改成驼峰式命名，如 user-sex 改为 userSex

```javascript
var dv = document.getElementById('dv')
var dt = dv.dataset;
var str = ''
str = dt.name + ',' + dt.age + ',' + dt.userSex;
dv.innerText = str;
```

#### 2.2.3 类名操作

**添加类**

```js
selector.classList.add("类名")
```

**删除类**

```js
selector.classList.remove("类名");
// 如果不写类名的话，删除的是选中节点的所有类
```

**切换类**

```JS
selector.classList.toggle("类名");
```

**包含类**

```js
selector.classList.contains("类名");
// 返回值是true或false
```

### 2.3 读取文件

通过 [`FileReader`](https://developer.mozilla.org/zh-CN/docs/Web/API/FileReader) 接口读取文件内容。


```html
<input type="file" id="f1">
<input type="submit" id="btn1" value="上传">
```

```js
var f1 = document.querySelector('#f1');
var btn1 = document.querySelector('#btn1');
btn1.onclick = function(){
    // 获取上传文件
    var fl1 = f1.files[0];
    // 读取文件，创建读取文件的对象
    var fReader = new FileReader();
    // 读取文件
    fReader.readAsText(fl1);
    // 开始读取文件的加载事件
    fReader.onload = function() {
        var style= document.createElement('style');
        var result = fReader.result;
        style.innerHTML = result;
        document.querySelector('head').appendChild(style)
    }
}
```
新建 style.txt 文件，编辑内容：
```css
#btn1{
    width: 70px;
    height: 30px;
    border: none;
    background-color: green;
    font-size: 14px;
    color: #fff;
}
```
运行程序，上传 style.txt 文件，查看样式变化。

### 2.4 网络状态检测

#### 2.4.1 navigator.onLine

```js
var state = window.navigator.onLine;
// 返回布尔值，网络联通为true，反之为false
if(state){
    alert('在线')
}else{
    alert('离线')
}
```

主流浏览器都支持。

#### 2.4.2 document.ononline

```js
window.ononline=function(){
    alert('连接上了')
}
window.onoffline=function(){
    alert('断网了')
}
```
浏览器支持情况：  

| 事件     | Chrome | IE                | Firefox | Safari | Opera |
| :------: | :----: | :---------------: | :-----: | :----: | :--: |
| ononline | 不支持 | IE8（IE11 已废弃） | 3.0     | 不支持 | 不支持 |

### 2.5 获取地理定位(不推荐)

```js
window.navigator.geolocation.getCurrentPosition(function(position){
    console.log(position)
},function(msg){
    console.log(msg) //获取失败返回相应信息
})
```
如果成功，则获取当前地理位置的经纬度。
```
position.coords.latitude  // 经度
position.coords.longitude // 纬度
```
> 注：若浏览器提示“获取您的位置”，请点击允许；
> 如果仍然报错"Network location provider at 'https://www.googleapis.com/' : No response received."，请 **科学上网**。

### 2.6 存储

随着互联网的快速发展，基于网页的应用越来越普遍，同时也变得越来越复杂，为了满足各种各样的需求，回经常性在本地存储大量的数据，传统方式我们以 `document.cookie` 来进行存储，但是由于其存储大小只有4K左右，并且解析也相当的复杂，给开发带来诸多不便，HTML5 规范则提出解决方案，使用 `sessionStorage` 和 `localStorage` 存储数据。

**HTML5存储的特性：**

1、设置，读取方法  
2、容量较大  
3、能存储字符串

**sessionStorage:**

1、关闭浏览器窗口生命周期结束  
2、在同一个窗口下数据可以共享  
3、容量约5M

**localStorage:**

1、永久有效，除非手动删除  
2、可以多窗口共享  
3、容量约20M

```js
// 设置session：属性名字，值
window.sessionStorage.setItem("name", "张三"); 
// 获取session的值
window.sessionStorage.getItem("name"); 
// 删除session
window.sessionStorage.removeItem("name");
// 清空session
window.sessionStorage.clear();

// 设置localStorage：属性名字，值
window.localStorage.setItem("name", "张三"); 
// 获取localStorage的值
window.localStorage.getItem("name"); 
// 删除localStorage
window.localStorage.removeItem("name");
// 清空localStorage
window.localStorage.clear();
```

### 2.7 其他

关于多媒体和canvas的应用，会在新文章中单独讲解，敬请期待……