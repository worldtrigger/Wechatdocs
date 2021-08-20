# 文件上传与下载

- 文件上传 API

- 文件下载 API

## 文件上传

- wx.uploadFile

| 属性     | 类型     | 是否必填 | 说明                                                               |
| -------- | -------- | -------- | ------------------------------------------------------------------ |
| url      | string   | 是       | 开发者服务器 url                                                   |
| filePath | string   | 是       | 要上传文件资源的路径                                               |
| name     | string   | 是       | 文件对应的 key,开发者在服务器端通过这个 key 可以获取文件二进制内容 |
| header   | Object   | 否       | HTTP 请求 header,header 中不能设置 Referer                         |
| formData | Object   | 否       | HTTP 请求中其他额外的 form data                                    |
| timeout  | number   | null     | 超时时间                                                           |
| success  | function | 否       | 接口调用成功的回调函数                                             |
| fail     | function | 否       | 接口调用失败的回调函数                                             |
| complete | function | 否       | 无论成功还是失败都执行                                             |

## 代码

- 必须和 chooseImage 搭配使用

```javascript
wx.chooseImage({
  count: 9, // 最多可以选择的图片张数，默认9
  sizeType: ['original', 'compressed'], // original 原图，compressed 压缩图，默认二者都有
  sourceType: ['album', 'camera'], // album 从相册选图，camera 使用相机，默认二者都有
  success: function (res) {
    var tempFilePaths = res.tempFilePaths;
    //创建uploadTask对象
    const uploadTask = wx.uploadFile({
      url: 'https://api.mofun365.com:8888/api/banner/wxUploadFile',
      filePath: tempFilePaths[0],
      name: 'file',
      header: {
        'content-type': 'Application/json',
      },
      formData: {
        imgName: '我是图片名称',
        imgSize: '122kb',
        position: 'wx', //自定义文件存放的文件夹
      },
      success: function (res) {
        console.log(res);
      },
    });
    //监听 HTTP Response Header 事件
    uploadTask.onHeadersReceived(function (res) {
      console.log('-----------监听 HTTP Response Header 事件-------------');
      console.log(res);
    });
    //取消监听 HTTP Response Header 事件
    uploadTask.offHeadersReceived(function () {
      console.log('-----------取消监听 HTTP Response Header--------------');
    });
    //监听上传进度变化事件
    uploadTask.onProgressUpdate(function (res) {
      console.log('-----------监听上传进度变化事件-------------');
      console.log(res);
    });
    //取消监听上传进度变化事件
    uploadTask.offProgressUpdate(function () {
      console.log('-----------取消监听上传进度变化事件--------------');
    });
    //中断请求任务
    //uploadTask.abort();
  },
});
```
