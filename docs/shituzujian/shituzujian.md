# 视图容器组件

- view 视图容器组件

- scroll-view 可滚动视图容器组件

- swiper 滑块视图容器组件

- movable-view 可移动视图容器组件

- cover-view 覆盖原生组件

## view 视图容器组件

- view 相当于 HTML 中的 div,他是块元素

| 属性             | 类型    | 默认值 | 功能                                                 |
| ---------------- | ------- | ------ | ---------------------------------------------------- |
| hover            | boolean | false  | 是否启用单机态                                       |
| hover-class      | string  | none   | 指定按下去的样式类,当 hover-class='none'没有单击效果 |
| hover-start-time | number  | 50     | 按住后多久出现单击态,单位毫秒                        |
| hover-stay-time  | number  | 400    | 手指松开后单击态保留事件,单位毫秒                    |

- 代码

```bash
<view class="view1"
hover="{{true}}"
hover-class="view1hover"
hover-start-time= "3000"
hover-stay-time= "5000"
>点击</view>


// 下面是css

.view1{
  width:100%;
  height:150rpx;
  background:yellow;
  text-align:center;
}
.view1hover{
  background:red;
}

```

## scroll-view 可滚动的视图区域组件

| 属性                    | 类型    | 默认值  | 功能                                                                                                           |
| ----------------------- | ------- | ------- | -------------------------------------------------------------------------------------------------------------- |
| scroll-x                | boolean | FALSE   | 允许横向滚动                                                                                                   |
| scroll-y                | boolean | FALSE   | 允许纵向滚动                                                                                                   |
| upper-threshold         | number  | 50      | 距离顶部左边多远时,触发 scrolltoupper 事件                                                                     |
| lower-threshold         | number  | 50      | 距底部右边多远时,触发 scrolltolower 事件                                                                       |
| scroll-top              | number  | null    | 设置竖向滚动条位置                                                                                             |
| scroll-left             | number  | null    | 设置横向滚动条位置                                                                                             |
| scroll-into-view        | string  | null    | 值应为某子元素 id,则滚动到该元素,元素顶部对齐滚动区域顶部                                                      |
| scroll-with-animation   | boolean | null    | 在设置滚动条位置时使用动画过渡                                                                                 |
| enable-back-to-top      | boolean | False   | IOS 顶部状态栏,安卓双击标题栏,滚动条返回顶部，只支持竖向                                                       |
| enable-flex             | boolean | FALSE   | 启用 FLEX 布局.开启后当前节点声明了 display:flex 就会成为 flex container 并作用于其孩子节点                    |
| scroll-anchoring        | boolean | FALSE   | 开启 scroll anchoring 特性即控制滚动位置不随内容变化而抖动,仅仅在 IOS 下生效,安装参考 css:overflow-anchor 属性 |
| refresher-enabled       | boolean | false   | 开启自定义下拉刷新                                                                                             |
| refresher-threshold     | number  | 45      | 设置自定义下拉刷新的阀值                                                                                       |
| refresher-default-style | string  | "black" | 设置自定义下拉刷新默认样式,支持设置 black， white , none ,none 表示不使用默认样式                              |
| refresher-background    | string  | "#FFF"  | 设置自定义下拉刷新区域背景颜色                                                                                 |
| refresher-triggered     | boolean | false   | 设置当前下拉刷新状态,true 表示已经触发下拉刷新,false 表示下拉刷新没有触发                                      |
| show-scrollbar          | boolean | true    | 滚动条显(隐)控制(同时开启 enhanced 属性后生效)                                                                 |
| paging-enabled          | boolean | false   | 分页滑动效果(同时开启 enhanced 属性后生效)                                                                     |
| fast-deceleration       | boolean | false   | 滑动减速速率控制(同时开启 enhanced 属性后生效)                                                                 |
| binddragstart           | event   | null    | 滑动开始事件(同时开启 enhanced 属性后生效)detail{scrollTop,scrollLeft}                                         |
| binddragging            | event   | null    | 滑动事件(同时开启 enhanced 属性后生效)detail{scrollTop,scrollLeft}                                             |
| binddragend             | event   | null    | 滑动事件结束(同时开启 enhanced 属性后生效)detail{scrollTop,scrollLeft}                                         |
| bindscrolltoupper       | event   | null    | 滚动到顶部/左边触发                                                                                            |
| bindscrolltolower       | event   | null    | 滚动到底部/右边触发                                                                                            |
| bindscroll              | event   | null    | 滚动时触发 event.detail = {scrollLeft, scrollTop, scrollHeight, scrollWidth, deltaX, deltaY}                   |
| bindrefresherpulling    | event   | null    | 自定义下拉刷新被下拉                                                                                           |
| bindrefresherrefresh    | event   | null    | 自定义下拉刷新被触发                                                                                           |
| bindrefresherrestore    | event   | null    | 自定义下拉被复位                                                                                               |
| bindrefresherabort      | event   | null    | 自定义下拉刷新被中止                                                                                           |

- 代码 竖向

`特别注意的就是scrollview盒子必须是固定值不能是百分比`

> scroll-into-view 必须是变量不能是死值,等加载完在设置

- wxml

```javascript
<!--pages/text/text.wxml-->
<view>
<view>{{message}}</view>
<view>{{globaldatamessage}}</view>
</view>

<view>{{ms1.result}}</view>

<scroll-view class="boxscrollview"
 scroll-y="{{true}}"
 bindscrolltoupper="upper"
 bindscrolltolower="lower"
 bindscroll="scroll"
 scroll-into-view="{{toView}}"
 scroll-top="{{scrollTop}}"  //滚动条位置
 scroll-with-animation="{{true}}"
>
 <view wx:for="{{dataall}}"
 wx:key="{{index}}" style="background:{{item.color}}"
 id="{{item.color}}"
class="scrollviewitem">序号{{item.id}}</view>
</scroll-view>

```

- wxjs

```javascript
// pages/text/text.js
const app = getApp();
Page({
  /**
   * 页面的初始数据
   */
  data: {
    dataall: [
      {
        id: 1,
        color: 'blue',
      },
      {
        id: 2,
        color: 'red',
      },
      {
        id: 3,
        color: 'green',
      },
      {
        id: 4,
        color: 'red',
      },
      {
        id: 5,
        color: 'black',
      },
    ],
    toView: '',
    scrollTop: '0',
    message: '这就是测试页面',
    globaldatamessage: app.globalData.testdata.message,
  },
  /*
    滚动到顶部触发
   */
  upper(e) {
    console.log('到了顶部');
    console.log(e);
  },
  /**
   *
   * @param {滚动到底部触发} options
   */
  lower(e) {
    console.log('滚动到底部触发');
    console.log(e);
  },
  scroll(e) {
    console.log('滚动中触发');
    console.log(e);
  },
  /**
   * 生命周期函数--监听页面加载
   */
  onLoad: function (options) {
    this.setData({
      toView: 'green',
    });
  },

  /**
   * 生命周期函数--监听页面初次渲染完成
   */
  onReady: function () {},

  /**
   * 生命周期函数--监听页面显示
   */
  onShow: function () {},

  /**
   * 生命周期函数--监听页面隐藏
   */
  onHide: function () {},

  /**
   * 生命周期函数--监听页面卸载
   */
  onUnload: function () {},

  /**
   * 页面相关事件处理函数--监听用户下拉动作
   */
  onPullDownRefresh: function () {},

  /**
   * 页面上拉触底事件的处理函数
   */
  onReachBottom: function () {},

  /**
   * 用户点击右上角分享
   */
  onShareAppMessage: function () {},
});
```

## swiper 滑块视图容器组件

| 属性                   | 类型    | 默认值        | 说明                                                                                                                                          |
| ---------------------- | ------- | ------------- | --------------------------------------------------------------------------------------------------------------------------------------------- |
| indicator-dots         | boolean | false         | 是否显示页面指示点                                                                                                                            |
| indicator-color        | color   | rgba(0,0,0.3) | 指示点颜色                                                                                                                                    |
| indicator-active-color | color   | #000000       | 当前选中的指示点颜色                                                                                                                          |
| autoplay               | boolean | false         | 是否自动切换                                                                                                                                  |
| current                | number  | 0             | 当前所在滑块的 index                                                                                                                          |
| interval               | number  | 5000          | 自动切换时间间隔                                                                                                                              |
| duration               | number  | 500           | 滑动动画时长                                                                                                                                  |
| circular               | boolean | false         | 是否衔接滑动                                                                                                                                  |
| vertical               | boolean | false         | 滑动方向是否为纵向                                                                                                                            |
| previous-margin        | string  | "0px"         | 前边距,可用于露出前一项的一小部分 接受 px 和 rpx 值                                                                                           |
| next-margin            | string  | "0px"         | 后边距,可用于露出后一项的一小部分,接受 px 和 rpx 的值                                                                                         |
| snap-to-edge           | boolean | false         | 当 swiper-item 的个数大于等于 2，关闭 circular 并且开启 previous-margin 或 next-margin 的时候，可以指定这个边距是否应用到第一个、最后一个元素 |
| display-multiple-items | number  | 1             | 同时显示的滑块数量                                                                                                                            |
| bindchange             | event   | null          | current 改变时会触发 change 事件，event.detail = {current, source}                                                                            |
| bindtransition         | event   | null          | swiper-item 的位置发生改变时会触发 transition 事件，event.detail = {dx: dx, dy: dy}                                                           |
| bindanimationfinish    | event   | null          | 动画结束时会触发 animationfinish 事件，event.detail 同上                                                                                      |

- 代码如下

```javascript
<swiper indicator-dots="={{true}}" autoplay="{{true}}" interval="{{3000}}" duration="{{300}}" indicator-color="blue"
indicator-active-color="yellow"
>
 <block wx:for="{{dataall}}">
  <swiper-item style="width:100%;height:300rpx;background:{{item.color}}">
   {{item.color}}
  </swiper-item>
 </block>
</swiper>
```

## movable-view 可移动视图容器组件

- 在页面中可以拖拽滑动.用的少。请参考文档

[文档看这里](https://developers.weixin.qq.com/miniprogram/dev/component/movable-view.html)

## cover-view 覆盖原生组件的视图容器
