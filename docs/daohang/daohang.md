# 小程序导航组件

- navigator 页面链接组件

- wx.navigateTo 保留当前页(还能跳回来)

- wx.redirectTo 关闭当前页跳转

- wx.switchTab 跳转到 tabbar 页面

- wx.navigateBack 返回上一页

- 设置导航条文字

- wx.reLaunch 关闭所有页面进行跳转

## 页面链接组件

```javascript
<navigator url="../xxx/xxx" open-type="navigate">保留当前页</navigator>

<navigator url="../xxx/xxx" open-type="switchTab">跳转到tabbar</navigator>

<navigator url="../xxx/xxx" open-type="redirect">关闭当前页跳转</navigator>
```

## 点击跳转

```javascript

<button bindtap="navigateBtn">保留当前页跳转</button>

<button bindtap="redirectBtn">关闭当前页跳转</button>

<button bindtap="switchBtn">跳转到tabbar页面</button>
```

## 绑定事件

- 路由跳转

```javascript
wx.navigateTo({
  url: 'xxxx',
  success: function (res) {
    console.log(res);
  },
  fail: function (res) {
    console.log(res);
  },
  complete: function () {
    //成功还是失败都执行
  },
});
```

- 关闭当前页跳转

```javascript
wx.redirectTo({
  url: 'xxxx',
  success: function (res) {
    console.log(res);
  },
  fail: function (res) {
    console.log(res);
  },
  complete: function () {
    //成功还是失败都执行
  },
});
```

- 底部导航

```javascript
wx.switchTab({
  url: 'xxxx',
  success: function (res) {
    console.log(res);
  },
  fail: function (res) {
    console.log(res);
  },
  complete: function () {
    //成功还是失败都执行
  },
});
```

- 返回页面

```javascript
wx.navigateBack({
  delta: 1, //返回的层级, 如果是1就是1级,如果是2就是2级
});
```

- 如果跳转后想要动态的设置标题

```javascript
wx.setNavigationBarTitle({
  title: '新改动的页面',
});
//显示加载小圆圈
wx.showNavigationBarLoading();
```
