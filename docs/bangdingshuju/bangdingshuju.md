# 小程序之绑定数据

> WXML 页面里的动态数据 都是来自 js 文件 Page 的 data,数据绑定就是通过双大括号将变量包裹起来,在 wxml 里面将数据显示出来

- js 里面

```javascript
Page({
  data: {
    message: 'Hello Mike',
    id: 2,
  },
});
```

- wxml 里面

```javascript
<view>{{ message }}</view>
<view class="item-{{id}}">{{message}}</view>
```

- 改变数据

```javascript
this.setData({
  message: '哈哈哈',
});
```

# 动态 class 绑定

```javascript
<view class="test {{isActive ? 'active':'' }}"></view>
```

# 控制属性绑定

```javascript
<view wx:if="{{flag}}"> 哈哈 </view>;

Page({
  data: {
    flag: true,
  },
});
```

# 关键字

- checkbox 没选中

```javascript
<checkbox checked="{{false}}"></checkbox>
```

# 运算绑定

```javascript
<view hidden="{{flag?true:false}}">Hidden</view>
<view>{{a+b}}+{{c}}+d</view>
<view wx:if="{{length>5}}"></view>
<view>{{"hello" + name}}</view>
```
