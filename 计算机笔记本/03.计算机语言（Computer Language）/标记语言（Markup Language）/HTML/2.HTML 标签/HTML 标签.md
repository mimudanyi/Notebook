# HTML 标签

参考网页：https://www.w3school.com.cn/tags/index.asp

## 文档

```html
<html>文档</html>
```

## 主体

```html
<body>主体</body>

属性
<body bgcolor="red">主体</body>	设置主体颜色为红色
<body backgroud="xxx.png">主体</body>	设置主体背景图片为xxx
```

## 标题

```html
<h1>标题1</h1>
<h2>标题2</h2>
<h3>标题3</h3>
<h4>标题4</h4>
<h5>标题5</h5>
<h6>标题6</h6>

<!--属性-->
	<h1 align="center"><!--拥有关于对齐方式的附加信息-->
        
```

## 段落

```html
<p>段落</p>
```

## 横线

```html
<hr/>
```

## 居中

```html
<center></center>
```

## 折行（换行）

```html
<br/>
```

## 超链接

```html
<a href="http://www.w3school.com.cn">This is a link</a>

属性
href可以是网址也可以是本地的路径
target="_blank" 开启一个新窗口
target="_self" 就进入自己这个窗口
target="_top" 顶级窗口
target="_parent" 父窗口

注：
超链接下面会有下划线
鼠标停留在超链接上鼠标会变成小手

图片超链接：
<a href="http://www.w3school.com.cn">
	<img src="w3school.jpg"/>
</a>
```

## 表格

```html
<!--三行三列-->

<table>
    <tr>
        <td></td>
        <td></td>
        <td></td>
    </tr>
    <tr>
        <td></td>
        <td></td>
        <td></td>
    </tr>
    <tr>
        <td></td>
        <td></td>
        <td></td>
    </tr>
</table>

属性：
<table border="1px">	设置表格的边框为 1 像素
<table width="300px">	设置表格的宽度为 300 像素
<table width="60%">	设置表格的宽度为页面的 60%
<table height="150px">	设置表格的高度为页面的 150 像素
    
<tr align="center">	设置行中文字居中（align为对齐方式）
    
<td rowspan="2">	设置行合并两格，向下
<tr colspan="2">	设置列合并两格
    
<th>也是单元格标签，可以用来做表格</th>
    
    <thead></thead>	头
    <tbody></tbody>	体
    <tfoot></tfoot>	脚
```

## 表单（form）【【【Java程序员必须搞懂这个！！！！！！】】】

```html
标签
<form>
    <input/>
</form>

属性
<form action="服务器地址">
<input type="">属性值：reset清空
<input value=""/>	格式的默认值
<input name="提交name的名称"/>	提交的数据！！！！！！【重点】，提交给服务器的形式是name=vale,只有name写了才会提交给服务器，当value没写的时候，提交的的是String="",即空字符串，不是null!!!!
    
<input disabled>	只读不能修改，同时也不能提交给服务器
<input readonly>    只读不能修改，可以提交给服务器
<input maxlength="3">    最多只能输入3个字符
```

表单示例

```html
<!DOCTYPE html>
<html>
	<head>
		<meta charset="utf-8">
		<title>罗童丹的网页</title>
	</head>
	<body>
		<center>
			<form action="C:\Users\23198\Desktop\zxc.txt" method="post" ><!-- post提交时不会显示表单信息 -->
				用户名：
				<input type="text" name="username"/>
				<br /><br />
				密码：
				<input type="text" name="password" />
				<br /><br />
				确认密码：
				<input type="text" />
				<br /><br />
				性别： 
				<input type="radio" name="gander" value="1" />男
				<input type="radio" name="gander" value="0" checked />女<!-- selected默认选中 -->
				<br /><br />
				兴趣爱好:
				<input type="checkbox" name="hobbies" value="smoking"/>抽烟
				<input type="checkbox" name="hobbies" value="drink" checked />喝酒<!-- selected默认选中 -->
				<input type="checkbox" name="hobbies" value="perm"/>烫头
				<br /><br />
				学历:
				<select name="grade" multiple="multiple" size="5">
					<!-- multiple属性表示支持多选，选择时要按住ctrl键 -->
					<!-- size属性表示多选框显示几个选项 -->
					<option value="">幼儿园</option>
					<option value="">小学</option>
					<option value="">初中</option>
					<option value="">高中</option>
					<option value="" selected >学士</option><!-- selected默认选中 -->
					<option value="">硕士</option>
					<option value="">博士</option>
				</select>
				<br /><br />
				简介:
				<textarea rows="10" cols="50" name="briefintroduction"></textarea><!-- 文本域 -->
				<br /><br />
				上传个人简历
				<input type="file" />
				<br><br />
				<!-- 隐藏域空间，不会显示，用户看不见，但是会提交 -->
				<input type="hidden" name="asdf" value="dsfa" />
				<input type="submit" value="注册" />
				<input type="reset" value="清空" />
			</form> 
		</center>
	</body>
</html>

```



## 图像

```html
<img src="w3school.jpg" width="104" height="142" title="我是个图片" alt="图片没找到"/>	只设置宽度时，高度会根据等比例缩放，反之同理
属性
title为鼠标悬停在图片上时显示的文字
alt为图片资源没有时显示的文字
```

## 列表

```html
无序列表
<ul>
    <li>xxxxxxxxxxxxxxxxxxxxx
        <ul>
            <li>xxxxxxxxxxxxxxxxxx</li>
            <li>xxxxxxxxxxxxxxxx</li>
            <li>xxxxxxxxxxxxxxxxxx</li>
		</ul>
    </li>
    <li>xxxxxxxxxxxxxxxxxx</li>
    <li>xxxxxxxxxxxxxxxxx</li>
</ul>
属性：
<ul type="disc">
</ul>
type:可以指定无序列表的开头是小实心圆圈还是小点点等


有序列表
<ol>
	<li></li>
    <li></li>
    <li></li>
</ol>

属性:
type="1"
```

## 注释

```html
<!--注释-->
```

## 水平线

```html
<hr/>
```

## 预留格式

```html
<pre>
	...
</pre>
```

## 实体符号

```
实体符号
&xxx;

&lt; <
&gt; >
&nbsp; 空格
```

## 图层

### div

```html
div会独自占用一行
```

### span

```html
span不会独自占用一行
```





