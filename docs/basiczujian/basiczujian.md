# 基础组件

- icon 图标组件

- text 文本组件

- progress 进度条组件

- rich-text 富文本组件

## icon 图标组件

| 属性  | 类型   | 默认值 | 说明                                           |
| ----- | ------ | ------ | ---------------------------------------------- |
| type  | string | null   | icon 的类型有 success,cancel,search,clear 等等 |
| size  | number | 23     | icon 的大小,单位 px                            |
| color | Color  | rgb 值 | icon 的颜色,同 css 的 color                    |

- 代码如下

```javascript
<icon type="search" size="48" color="red"></icon>
```

## 文本组件

- 支持转义符 "\"

| 属性       | 类型    | 默认值 | 说明         |
| ---------- | ------- | ------ | ------------ |
| selectable | boolean | FALSE  | 文本是否可选 |
| space      | string  | null   | 显示连续空格 |
| decode     | boolean | FALSE  | 是否解码     |

- 代码

```javascript
<text selectable="true" decode="{{true}}">
  哈哈哈\r\n呵呵呵
</text>
```

## 进度条组件

| 属性            | 类型          | 默认值  | 说明                      |
| --------------- | ------------- | ------- | ------------------------- |
| percent         | number        | 无      | 百分比 0~100              |
| show-info       | boolean       | False   | 在进度条右侧显示百分比    |
| border-radius   | number/string | 0       | 圆角大小                  |
| font-size       | number/string | 16      | 右侧百分比大小            |
| color           | string        | #09BB07 | 进度条颜色                |
| activeColor     | string        | #09BB07 | 已选择的进度条颜色        |
| backgroundColor | string        | #EBEBEB | 未选择的进度条的颜色      |
| active          | boolean       | FALSE   | 进度条从左往右的动画      |
| duration        | number        | 30      | 进度增加 1%所需要的毫秒数 |
| bindactiveend   | event         | null    | 动画完成事件              |
| stroke-width    | number        | 无      | 进度条的宽度              |

```html
<progress
  percent="50"
  show-info="50%"
  border-radius="30"
  backgroundColor="#002266"
  activeColor="yellow"
  stroke-width="20"
></progress>
```

## rich-text 富文本组件(用的太少)

rich-text 通过这个组件可以在 wxml 页面显示一些富文本的内容,比如 HTML 一些元素内容显示

```javascript
<rich-text nodes="<h1>我爱你</h1>">哈哈哈</rich-text>
```
