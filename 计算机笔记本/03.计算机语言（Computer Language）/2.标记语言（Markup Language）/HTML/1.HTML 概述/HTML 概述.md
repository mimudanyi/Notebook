# HTML 概述

## 一、简介

超文本标记语言（Hyper Text Markup Language，HTML）是一种构建网页的标准标记语言。

- 标记语言是一套标记标签 (markup tag)，HTML 全部是由标记标签组成的，这些标签用来表述网页的结构特点。
- 超文本：可以展示动画、图片、音视频多媒体等内容，还可以进行文本之间的跳转。
- 不区分大小写
- 语法松散不严格

HTML 与 CSS、JavaScript 通常一起组合使用、来完成网页、网页应用程序、移动应用程序界面的开发。

HTML 是构建一个网页的基础，CSS 会让网页变得更好看，JavaScript 会让网页实现更多的交互行为。同时 CSS 和JavaScript 都可以嵌入 HTML 的结构中。所以 HTML 在网页开发中是非常重要的。

## 三、HTML 元素

指的是从开始标签（start tag）到结束标签（end tag）的所有代码。

开始标签：常被称为开放标签（opening tag）。

结束标签：常称为闭合标签（closing tag）。

## 四、HTML 属性：

- HTML 标签可以拥有属性。属性提供了有关 HTML 元素的更多的信息。
- 属性总是以名称/值对的形式出现，比如：name="value"。
- 属性总是在 HTML     元素的开始标签中规定。
- 始终为属性值加引号，属性值应该始终被包括在引号内。双引号是最常用的，不过使用单引号也没有问题。在某些个别的情况下，比如属性值本身就含有双引号，那么您必须使用单引号，例如：name='Bill     "HelloWorld" Gates'

## 五、HTML 文档 = 网页

- HTML 文档描述网页
- HTML 文档包含 HTML     标签和纯文本
- HTML 文档也被称为网页
- Web 浏览器的作用是读取HTML     文档，并以网页的形式显示出它们。浏览器不会显示 HTML 标签，而是使用标签来解释页面的内容：

## 六、基本结构

```html
< !DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <title>第一个网页</title>
</head>

<body>
	<1>Hello World!</1>
</body>

</html>
```

