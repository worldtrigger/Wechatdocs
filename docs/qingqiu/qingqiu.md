# 请求服务器数据 API

- wx.request

```javascript
wx.request({
  url: 'xxx.php',
  method: 'POST',
  data: {
    x: '',
    y: '',
  },
  header: {
    'content-type': 'application/json',
  },
  success: function (res) {
    console.log(res.data);
  },
});
```

| 属性     | 类型                       | 必填 | 说明                                                                                                              |
| -------- | -------------------------- | ---- | ----------------------------------------------------------------------------------------------------------------- |
| url      | string                     | 是   | 开发者服务器接口地址                                                                                              |
| data     | string/object/Array/Buffer | 否   | 请求的参数                                                                                                        |
| header   | object                     | 否   | 设置请求的 header,header 中不能设置 Referer,content-type 默认为 application/json                                  |
| method   | string                     | 否   | 默认为 GET,有效值 OPTIONS,GET,HEAD,POST,PUT,DELETE,TRACE,CONNECT                                                  |
| dataType | string                     | 否   | 默认为 json 设置了 dataType 为 json 则会尝试对响应的数据做一次 JSON.parse,设置其他的不对返回的内容进行 JSON.parse |
| success  | function                   | 否   | 成功收到数据返回的回调函数                                                                                        |
| fail     | function                   | 否   | 接口调用失败的回调函数                                                                                            |
| complete | function                   | 否   | 无论成功与否 都执行                                                                                               |
