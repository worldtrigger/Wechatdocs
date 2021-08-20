# 小程序脚本语言

## 介绍

WXS(wx script) 是小程序的一套脚本语言,结合 WXML 页面文件,可以构建出页面的结构,他把原来放在 js 文件处理的逻辑,可以直接放在 wxml 页面文件里直接进行处理

两种使用方式: 一种是 wxs 脚本语言嵌入到 WXML 页面文件里,在 WXML 文件中<wxs>标签内用来处理相关逻辑,另外一种是以 .wxs 后缀结尾的文件独立存在,然后在引入到 wxml 页面文件里使用

## 举例

### 本页面使用

- 代码放在 wxml

```javascript

<wxs module="ms1">
  var msg = "测试数据"
  module.exports={
    result:msg
  }
</wxs>
```

> module 里面的 ms1 可以随便写

- 使用的时候,前面就是模块名称

```javascript
<view>{{ms1.result}}</view>
```

### 写在 wxs 文件里面

- 新建 text.wxs 文件

```javascript
var msg = '测试数据';
module.exports = {
  result: msg,
};
```

- 页面里面想引入这个文件的时候,必须起个模块名称

```javascript
<wxs src="text.wxs" module="ms1"></wxs>
```

- 调用页面数据的时候

```javascript
<view>{{ms1.result}}</view>
```

## 特别注意的就是

wxs 之间调用模块只能通过 export 输出,再通过 require 调用

- a.wxs

```javascript
var foo = 'hello world';

module.exports = {
  footer: foo,
};
```

- 调用的时候 b.wxs

```javascript
var tools = require('a.wxs');
console.log(tools.footer);
```
