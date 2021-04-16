# HTML 事件

HTML 事件可以是浏览器行为，也可以是用户行为。

HTML 网页中的每个元素都可以产生某些可以触发 JavaScript 函数的事件。

以下是 HTML 事件的实例：

- HTML 页面完成加载
- HTML input 字段改变时
- HTML 按钮被点击

通常，当事件发生时，你可以做些事情。

在事件触发时 JavaScript 可以执行一些代码。

HTML 元素中可以添加事件属性，使用 JavaScript 代码来添加 HTML 元素。

单引号:

```js
 <some-HTML-element some-event='some JavaScript'>
```

双引号:

```js
 <some-HTML-element some-event="some JavaScript">
```

在以下实例中，按钮元素中添加了 onclick 属性 (并加上代码):

```html
<!DOCTYPE html>
<html>
<head> 
<meta charset="utf-8"> 
<title>W3Cschool教程(w3cschool.cn)</title> 
</head>
<body>

<button onclick="getElementById('demo').innerHTML=Date()">现在的时间是?</button>
<p id="demo"></p>

</body>
</html>
```

## 常见的HTML事件

下面是一些常见的HTML事件的列表:

| 事件        | 描述                         |
| :---------- | :--------------------------- |
| onchange    | HTML 元素改变                |
| onclick     | 用户点击 HTML 元素           |
| onmouseover | 用户在一个HTML元素上移动鼠标 |
| onmouseout  | 用户从一个HTML元素上移开鼠标 |
| onkeydown   | 用户按下键盘按键             |
| onload      | 浏览器已完成页面的加载       |