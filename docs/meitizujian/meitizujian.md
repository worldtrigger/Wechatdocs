# 小程序媒体组件

- audio 音频组件

- image 组件

- video 视频组件

- camera 相机组件

## audio 组件

```javascript
<audio
  poster="{{poster}}" //封面地址
  name="{{name}}"
  author="{{author}}"
  src="{{src}}"
  id="myAudio"
  controls
  loop
></audio>

----

Page({
  onReady:function(e){
    this.audioCtx = wx.createAudioContext('myAudio')
  }
})
```

## image 图片组件

```javascript
<image
  style="width: 200px; height: 200px; background-color: #eeeeee;"
  mode="{{item.mode}}"
  src="{{src}}"
></image>
------page-----

    array: [{
      mode: 'scaleToFill',
      text: 'scaleToFill：不保持纵横比缩放图片，使图片完全适应'
    }, {
      mode: 'aspectFit',
      text: 'aspectFit：保持纵横比缩放图片，使图片的长边能完全显示出来'
    }, {
      mode: 'aspectFill',
      text: 'aspectFill：保持纵横比缩放图片，只保证图片的短边能完全显示出来'
    }, {
      mode: 'top',
      text: 'top：不缩放图片，只显示图片的顶部区域'
    }, {
      mode: 'bottom',
      text: 'bottom：不缩放图片，只显示图片的底部区域'
    }, {
      mode: 'center',
      text: 'center：不缩放图片，只显示图片的中间区域'
    }, {
      mode: 'left',
      text: 'left：不缩放图片，只显示图片的左边区域'
    }, {
      mode: 'right',
      text: 'right：不缩放图片，只显示图片的右边边区域'
    }, {
      mode: 'top left',
      text: 'top left：不缩放图片，只显示图片的左上边区域'
    }, {
      mode: 'top right',
      text: 'top right：不缩放图片，只显示图片的右上边区域'
    }, {
      mode: 'bottom left',
      text: 'bottom left：不缩放图片，只显示图片的左下边区域'
    }, {
      mode: 'bottom right',
      text: 'bottom right：不缩放图片，只显示图片的右下边区域'
    }],

```

## video 视频组件

```javascript
<video
  id="myVideo"
  src="http://wxsnsdy.tc.qq.com/105/20210/snsdyvideodownload?filekey=30280201010421301f0201690402534804102ca905ce620b1241b726bc41dcff44e00204012882540400&bizid=1023&hy=SH&fileparam=302c020101042530230204136ffd93020457e3c4ff02024ef202031e8d7f02030f42400204045a320a0201000400"
  danmu-list="{{danmuList}}"
  enable-danmu
  danmu-btn
  controls
></video>
```

## camera 相机组件

```javascript
<camera
  device-position="back"
  flash="off"
  binderror="error"
  style="width: 100%; height: 300px;"
></camera>
```
