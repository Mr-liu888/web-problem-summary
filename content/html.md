# [返回主页](https://github.com/Mr-liu888/web-problem-summary/blob/main/README.md)

<b><details><summary>1. 总结HTML5新特新</summary></b>

## 一. 语义化标签

**1.使用语义化标签的原因/优点:**

根据内容的结构化使用语义化标签，能够使开发者更好的阅读和理解以及浏览器爬虫与搜索引擎解析。

**2. 语义话标签集合**

新block标签：header,footer,main,aside,article,section,nav,hgroup（主要8个）。
新表单标签：date、time、email、url、search
媒介标签： video 和 audio
绘画标签： canvas

**3.一些新标签的详细语义（兼容性好的标签）**

header:页眉（网页（部分区域）的头部 顶部 导航区域等等）;
footer:页脚（网页（部分区域）的底部|版权区域等等）;
section 标签定义网页中的区域（部分）；
article 内容是引用其他地方的；
aside 跟 article 是一起使用；是辅助 article 区域的内容;
nav 导航链接部分;
hgroup 给标题分组，不能就一个标题;
figure 对多个元素进行组合。通常与figcaption联合使用;

**4.video标签的用法介绍**

    <video>
         <source src="res/birds.mp4">
         <source src="res/birds.ogg">
         <source src="res/birds.webm">
         您的浏览器不支持VIDEO播放！
    </video>


它本身是一个300*150的inline-block元素

VIDEO标签/对象常用的成员：


**(1)、成员属性**

①、autoplay：false，是否自动播放

②、controls：false，是否显示播放控件,不同浏览器的播放控件不一样

③、loop：false，是否循环播放

④、muted：false，是否静音播放

⑤、poster："''，在播放第一帧之前显示的海报

⑥、preload：视频的预加载策略，可取值：

A、auto：预加载视频的元数据以及缓冲一定时长

B、metadata：仅预加载视频的元数据(尺寸、时长、第一帧内容)，没有视频缓冲

C、none：不预加载任何数据

**以下为JS对象属性,不能用于标签**

①、currentTime：当前播放的时长

②、duration：总时长

③、paused：true，当前视频是否处于暂停状态

④、volume：1，当前音量

⑤、playbackRate：1，回放速率，大于1表快放，小于1表慢放

**(2)、成员方法**

①、play( )： 播放视频

②、pause( )： 暂停播放

**(3)、成员事件**

①、onplay：当视频开始播放时触发的事件

②、onpause：当视频开始暂停时触发的事件


**5.audio标签详解(苹果IOS10不支持,可用video代替）**

    <audio>
         <source src="res/bg.mp3">
         <source src="res/bg.ogg">
         <source src="res/bg.wav">
         您的浏览器不支持AUDIO播放！
    </audio>

默认是一个300*30的inline-block元素，但若没有controls属性,则display:none

AUDIO标签/对象常用的成员：

**(1)、成员属性：**

①、autoplay：false，是否自动播放

②、controls：false，是否显示播放控件

③、loop：false，是否循环播放

④、muted：false，是否静音播放

⑤、preload：视频的预加载策略，可取值

A、auto：预加载视频的元数据以及缓冲一定时长

B、metadata：仅预加载视频的元数据(尺寸、时长、第一帧内容)，没有视频缓冲

C、none：不预加载任何数据

**以下为JS对象属性,不能用于标签**

①、currentTime：当前播放的时长

②、duration：总时长

③、paused：true，当前视频是否处于暂停状态

④、volume：1，当前音量

⑤、playbackRate：1，回放速率，大于1表快放，小于1表慢放

**(2)、成员方法**

①、play( )： 播放视频

②、pause( )： 暂停播放

**(3)、成员事件**

①、onplay：当视频开始播放时触发的事件

②、onpause：当视频开始暂停时触发的事件


**6.Canvas标签详解**

Canvas：画布，是H5提供的2D绘图技术

    <canvas width="500" height="400">
         您的浏览器不支持Canvas标签！
    </canvas>

canvas标签在浏览器中默认是300*150的inline-block

画布的宽和高只能使用HTML/JS属性来赋值，不能使用CSS样式(style)赋值

每个画布上有且只有一个“画笔”对象，称为“绘图上下文”对象，使用该对象进行绘图

    var ctx = canvas.getContext('2d')  //得到画布上的画笔对象

**(1)、使用Canvas绘制矩形，矩形的定位点在自己的左上角**

①、`ctx.lineWidth = 1`

描边宽度

②、`ctx.fillStyle = '#000'`

填充样式/颜色

③、`ctx.strokeStyle = '#000'`

描边样式/颜色

④、`ctx.fillRect( x, y, w, h )`

填充一个矩形

⑤、`ctx.strokeRect( x, y, w, h )`

描边一个矩形

⑥、`ctx.clearRect( x, y, w, h )`

清除一个矩形范围内所有的绘图

**(2)、使用Canvas绘制文本**

一段文字的定位点在其文本基线的起点

①、`ctx.textBaseline = 'top'`

文本基线改为顶端起始

②、`ctx.font = '12px sans-serif'`

文本大小和字体

③、`ctx.fillText( str, x, y )`

填充一段文本

④、`ctx.strokeText( str, x, y )`

描边一段文本

⑤、`ctx.measureText( str )`

基于当前文字大小字体设置测量文本，返回一个有用对象：{width: x},可以实现绘制文本右对齐,使用时ctx.measureText( str ).width


**(3)、Canvas绘图中使用渐变对象**

(a)、线性渐变：linearGradient

(b)、径向渐变：radialGradient

可以参考PS中的渐变效果。

// 创建渐变区域

    var g = ctx.createLinearGradient( x1, y1,  x2,  y2 );

// 创建渐变节点

    g.addColorStop( offset,  color );

// 创建渐变节点

    g.addColorStop( offset,  color );

// 使用渐变对象

    ctx.strokeStyle = g; 

// 使用渐变对象

    ctx.fillStyle = g;  

**示例  https://www.jianshu.com/p/63d0ecbcc4a7**


**(4)、使用Canvas进行绘图 — 路径**

类似于PS中的“钢笔工具”，由多个坐标点组成的任意形状，路径不可见，可用于“描边”、“填充”、“裁剪”

①、`ctx.beginPath()`

开始一条新路径

②、`ctx.closePath()`

闭合当前路径

③、`ctx.moveTo(x, y)`

移动到指定点

④、`ctx.lineTo(x, y)`

从当前点到指定点画直线

⑤、`ctx.arc(cx, cy, r, start, end)`

绘制圆拱路径

⑥、`ctx.stroke()`

对当前路径描边

⑦、`ctx.fill()`

对当前路径填充

⑧、`ctx.clip()`

使用当前路径进行裁剪


**(5)、Canvas绘图核心知识点总结**

①、绘制矩形：

ctx.fillRect()  ctx.strokeRect()   ctx.clearRect()

②、绘制文本：

ctx.fillText()  ctx.strokeText()   ctx.measureText().width

③、绘制路径：

ctx.beginPath()   ctx.closePath()   ctx.moveTo()  ctx.lineTo()   ctx.arc()   ctx.stroke()  ctx.fill()   ctx.clip()

## 二、HTML5新特性 —— WebStorage

在浏览器中存储当前用户专有的数据：访问历史、内容定制、样式定制...

在客户端存储数据可以使用的技术：

(1)、Cookie技术：浏览器兼容性好；不能超过4KB，操作复杂

(2)、Flash存储：依赖于Flash播放器

(3)、H5 WebStorage：不能超过8MB，操作简单

(4)、IndexedDB：可存大量数据，还不是标准技术



Session：会话，浏览器从打开某个网站的一个页面开始，中间可能打开很多页面，直到关闭浏览器，整个过程称为“浏览器与Web服务器的一次会话”

WebStorage技术中，浏览器为用户提供了两个对象：

(1)、window.sessionStorage：类数组对象，会话级数据存储

在浏览器进程所分得的内存存储着一次Web会话可用的数据，可供此次会话中所有的页面共同使用；浏览器一旦关闭就消失了

作用：在同一个会话中的所有页面间共享数据，如登录用户名

// 保存一个数据

sessionStorage[key] = value

// 保存一个数据

sessionStorage.setItem(key, value)

// 读取一个数据

var v = sessionStorage[key]

// 读取一个数据

var v = sessionStorage.getItem(key)

// 删除一个数据

sessionStorage.removeItem(key)

// 清除所有数据

sessionStorage.clear()

// 数据的数量

sessionStorage.length

// 获取第i个key

sessionStorage.key(i)

(2)、window.localStorage：类数组对象，本地存储(跨会话级存储)

在浏览器所能管理的外存(硬盘)中存储着用户的浏览数据，可供此次会话以及后续的会话中的页面共同使用；即使浏览器关闭也不会消失——永久存在

作用：在当前客户端所对应的所有会话中共享数据，如登录用户名

// 保存一个数据

localStorage[key] = value

// 保存一个数据

localStorage.setItem(key, value)

// 读取一个数据

var v = localStorage [key]

// 读取一个数据

var v = localStorage.getItem(key)

// 删除一个数据

localStorage.removeItem(key)

// 清除所有数据

localStorage.clear()

// 数据的数量

localStorage.length

// 获取第i个key

localStorage.key(i)

localStorage中若数据发生了修改，会触发一次window.onstorage事件，可以监听此事件，实现监视localStorage数据改变的目的，用于在一个窗口中监视其它窗口中对localStorage数据的修改——不能监视sessionStorage数据的修改

</details>
