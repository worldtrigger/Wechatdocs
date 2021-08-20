# 小程序生命周期函数和注册数据

## 生命周期函数

微信小程序有 10 大钩子函数

每个钩子函数只可以写一次,要是多次写 以最后一个为准

### onLoad

- 监听页面加载

- 一般页面之间传值会用得上

```javascript
  /**
   * 生命周期函数--监听页面加载
   */
  onLoad: function (options) {
    console.log(options)
  },
```

### onReady

- 监听页面初次渲染完成(组件加载完毕)

```javascript
  /**
   * 生命周期函数--监听页面初次渲染完成
   */
  onReady: function () {

  },
```

### onShow

- 监听页面显示

```javascript
  /**
   * 生命周期函数--监听页面显示
   */
  onShow: function () {

  },
```

### onHide

- 监听页面隐藏

```javascript
  /**
   * 生命周期函数--监听页面隐藏
   */
  onHide: function () {

  },
```

### onUnload

- 监听页面卸载

```javascript
  /**
   * 生命周期函数--监听页面卸载
   */
  onUnload: function () {

  },
```

### onPullDownRefresh

- 监听用户下拉动作

```javascript
  /**
   * 页面相关事件处理函数--监听用户下拉动作
   */
  onPullDownRefresh: function () {

  },
```

### onReachBottom

- 监听上拉触底事件

```javascript
  /**
   * 页面上拉触底事件的处理函数
   */
  onReachBottom: function () {

  },

```

### onShareAppMessage

- 监听用户右上角分享

```javascript
  /**
   * 用户点击右上角分享
   */
  onShareAppMessage: function () {

  }
```

### onPageScroll

- 监听页面滚动事件

```javascript

onPageScroll(){

}

```

### onResize

- 页面尺寸事件

```javascript

onResize(res){

}

```

## 注册数据使用 data

```javascript
  /**
   * 页面的初始数据
   */
  data: {
    message: "这就是测试页面",
    globaldatamessage:app.globalData.testdata.message
  },
```

### 修改 data 里面的数据

```javascript
this.setData({
  message: 'xxx', //属性名:值的
});
```
