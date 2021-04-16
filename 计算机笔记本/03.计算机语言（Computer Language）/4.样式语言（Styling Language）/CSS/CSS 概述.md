# CSS 概述

## 一、定义

Cascading Style Sheets（层叠样式表，CSS） 是一种描述 HTML 文档样式的语言。CSS 描述应该如何显示 HTML 元素。

- CSS 描述了*如何在屏幕、纸张或其他媒体上显示 HTML 元素*
- CSS *节省了大量工作*。它可以同时控制多张网页的布局
- 外部样式表存储在 *CSS 文件*中

## 二、插入样式表的方法

### 2.1 内联样式（Inline style）

```html
<标签 style="样式值:样式名;样式值样式名;...">XXXX</标签>
```

### 2.2 内部样式块（Internal     style sheet）

选择器

- id 选择器：【#id】
- 标签选择器：【标签名】
- 类选择器：【.类名】（在标签中有一个属性为class，给其赋值就可以了）

```html
<head>
    <style type="text/css">
        选择器{
            样式名:样式值;
            样式名:样式值;
            样式名:样式值;
        }
        选择器{
            样式名:样式值;
            样式名:样式值;
            样式名:样式值;
        }
        选择器{
            样式名:样式值;
            样式名:样式值;
            样式名:样式值;
        }
    </style>
</head>
```

### 2.3 外部样式表（External     style sheet）

引入的方法

```html
<head>
    ...
    <link type="text/css" rel="stylesheet" href="css文件的路径" />
</head>

```

.css 文件的写法

选择器

- id 选择器：【#id】
- 标签选择器：【标签名】
- 类选择器：【.类名】（在标签中有一个属性为class，给其赋值就可以了）

```css
选择器{
            样式名:样式值;
            样式名:样式值;
            样式名:样式值;
        }
```

## 三、注释

```css
/*
	注释
*/
```

