# 微信小程序模板和引用

## 定义模板

wxml 提供模板(template) 可以在模板中定义代码片段,然后在不同的地方引用

```javascript
<template name="msgitem">
  <view>
    <text>
      {{ item.index }} :{{ item.msg }}
    </text>
    <text>Time:{{ item.time }}</text>
  </view>
</template>
```

- 使用的时候

```javascript

<template is="msgitem" data="{{item}}">

```

## 模板引用

- import 可以在该文件中使用目标文件定义的 template

```javascript
<import src="item.wxml"/>
<template is="item" data="{{text:'forbar'}}">
```

> 特别注意的就是 import 也是有作用域的概念。即只会 import 目标文件中定义的 template,而不会 import 目标文件 import 的 template 比如 c 引用了 B ,B 引用了 A,那么在 C 中不可以使用 A 定义的模板

- include 可以将目标文件除了 template 的整个代码引入,相当于拷贝到 include 位置

```javascript
<include src="header.wxml">
```
