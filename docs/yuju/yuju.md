# 小程序控制语句

- 条件渲染

- 列表渲染

## 条件渲染

`用wx:if="{{flag}}"来判断是否渲染代码块`

- 代码模板

```javascript
<view wx:if="{{flag}}"> True </view>
```

- 使用的时候

```javascript
<block wx:if="{{true}}">
  <view>1</view>
  <view>2</view>
</block>
<block wx:else>
 第二种可能
</block>
```

## hidden 和 if 对比

- if 为真才渲染,假就不渲染

- hidden 就简单得多,组件始终被渲染,只是简单的控制显示和隐藏

`hidden 仅仅只对块元素生效 flex,span都不生效`

## 列表渲染

在组件上使用 wx:for 控制属性绑定一个数组,即可使用数组中各项数据重复渲染

- 默认选项

```javascript
<view wx:for="{{array}}" wx:key="{{index}}">
  <text>
    {{ index }} --- {{ item }}
  </text>
</view>
```

- 指定选项 index,item

```javascript
<view wx:for="{{arr}}" wx:for-index="i" wx:for-item="content" wx:key="{{i}}">
  序号{{ i }} --- 内容{{ content }}
</view>
```
