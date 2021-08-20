# 小程序路由

| 页面路由方式 | 触发时机               | 路由后页面    | 路由前页面                                          |
| ------------ | ---------------------- | ------------- | --------------------------------------------------- |
| 初始化       | 小程序打开的第一个页面 | onLoad,onShow | 空                                                  |
| 打开新页面   | wx.navigateTo          | onLoad,onShow | onHide                                              |
| 页面重定向   | wx.redirectTo          | onLoad,onShow | onUnload                                            |
| 页面返回     | wx.navigateBack        | onShow        | onUnload(多层页面返回每个页面会按顺序触发 onUnload) |
| tab 切换     | wx.switchTab           | onLoad,onShow | 空                                                  |
| 重启动       | wx.relaunch            | onLoad,onShow | onUnload                                            |

# 代码举例

## wx.navigateTo

### 传递的是值类型

- 发送数据

```javascript
wx.navigateTo({
  url: '../test/test?str=' + str,
  success: function (res) {},
  fail: function (res) {},
  complete: function (res) {},
});
```

- 接受数据

```javascript
// test.js
onLoad: function(options) {
    var str = options.str

    this.setData({
      str: str
    })
  }
```

### 传递的是地址引用类型

- 发送数据

```javascript
// index.js
onClick: function (e) {
    var obj = JSON.stringify(myObj) //myObj：本js文件中的对象
    wx.navigateTo({
      url: '../test/test?obj=' + obj,
      success: function(res) {},
      fail: function(res) {},
      complete: function(res) {},
    })
  }
```

- 接收数据

```javascript
// test.js
onLoad: function(options) {
    var obj =JSON.parse(options.obj）
//  testObj:本js文件中的对象
    this.setData({
      testObj: obj
    })
  }
```

## 传递的是特殊符号

> 如果对象的参数或数组的元素中遇到地址，地址中包括?、&这些特殊符号时，对象/数组先要通过 JSON.stringify 转化为字符串再通过 encodeURIComponent 编码，接收时，先通过 decodeURIComponent 解码再通过 JSON.parse 转换为 JSON 格式的对象/数组

- 发送数据

```javascript
// index.js
onClick: function (e) {
    var obj = JSON.stringify(myObj) //myObj：本js文件中的对象
    wx.navigateTo({
      url: '../test/test?obj=' + encodeURIComponent(obj), // 进行编码
      success: function(res) {},
      fail: function(res) {},
      complete: function(res) {},
    })
  }
```

- 接收数据

```javascript
// test.js
onLoad: function(options) {
    var obj =JSON.parse(decodeURIComponent(options.obj))
//  testObj:本js文件中的对象
    this.setData({
      testObj: obj
    })
  }
```
