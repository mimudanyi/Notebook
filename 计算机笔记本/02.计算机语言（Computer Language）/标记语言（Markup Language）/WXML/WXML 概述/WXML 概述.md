# WXML

WXML（WeiXin Markup Language）是框架设计的一套标签语言，结合基础组件、事件系统，可以构建出页面的结构。

用以下一些简单的例子来看看 WXML 具有什么能力：

## 一、数据绑定

```html
<!--wxml-->
<view> {{message}} </view>
// page.js
Page({
  data: {
    message: 'Hello MINA!'
  }
})
```

## 二、列表渲染

```html
<!--wxml-->
<view wx:for="{{array}}"> {{item}} </view>
// page.js
Page({
  data: {
    array: [1, 2, 3, 4, 5]
  }
})
```

## 三、条件渲染

```html
<!--wxml-->
<view wx:if="{{view == 'WEBVIEW'}}"> WEBVIEW </view>
<view wx:elif="{{view == 'APP'}}"> APP </view>
<view wx:else="{{view == 'MINA'}}"> MINA </view>
// page.js
Page({
  data: {
    view: 'MINA'
  }
})
```

## 四、模板引用

```html
<!--wxml-->
<template name="staffName">
  <view>
    FirstName: {{firstName}}, LastName: {{lastName}}
  </view>
</template>

<template is="staffName" data="{{...staffA}}"></template>
<template is="staffName" data="{{...staffB}}"></template>
<template is="staffName" data="{{...staffC}}"></template>
// page.js
Page({
  data: {
    staffA: {firstName: 'Hulk', lastName: 'Hu'},
    staffB: {firstName: 'Shang', lastName: 'You'},
    staffC: {firstName: 'Gideon', lastName: 'Lin'}
  }
})
```

### 4.1 文件引用

- import
- include