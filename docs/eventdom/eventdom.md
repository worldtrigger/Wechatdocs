# 小程序事件传值

> 事件传值全靠 e 这个对象

- 给组件节点增加属性:data 属性='属性值'

- 获取参数在事件里面的获取事件 e,当前元素属性 currentTarget

`在wxml中,这些自定义数据以data-开头,多个单词由连字符-`

## 点击事件

```bash

<view bindtap="demo" data-id="123" data-val="你好"> 新闻1</view>
<view bindtap="demo" data-id='456'>新闻2</view>
<view bindtap="demo" data-id="789">新闻3</view>

<view bindtap="demo" data-user-name='aaa'>data属性驼峰命名</view>
<view bindtap="demo" data-username="aaa">data属性小写字母</view>

```

- 点击事件:

```bash
demo:function(e){
   console.log(e)
}
```

## 获取值

```javascript
target 对应的是触发事件的源头组件,这个组件有可能是子组件,有可能是父组件,主要是执行动作的区域.而currentTarget始终对应事件所绑定的组件
```
