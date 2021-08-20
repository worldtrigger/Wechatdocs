# 小程序表单

- button 按钮组件

- checkbox 多项选择器组件

- radio 单选选择器组件

- input 单行输入框组件

- textarea 多行输入框组件

- label 改进表单可用性组件

- picker 滚动选择器组件

- slider 滑动选择器组件

- switch 开关选择器组件

- form 表单组件

- editor 富文本组件

## button 组件

| 属性      | 类型    | 默认值  | 说明                                                          |
| --------- | ------- | ------- | ------------------------------------------------------------- |
| size      | string  | Default | 按钮的大小,有效值 default,mini                                |
| type      | string  | Default | 按钮的样式类型,有效值,基本类型 primary,默认类型 default       |
| disabled  | boolean | False   | 是否禁用                                                      |
| form-type | string  | 无      | 有效值 submit,reset 用于 form 组件,单击触发 submit/reset 事件 |
| open-type | string  | 否      | 微信开放能力:见 open-type 合法值                              |

```html
<button size="32" loading="{{true}}"></button>
```

## checkbox 多项选择器组件

- checkbox 多项选择器 ,checkbox-group 由多个 checkbox 组成

| 属性     | 类型    | 默认值 | 说明                                                                      |
| -------- | ------- | ------ | ------------------------------------------------------------------------- |
| value    | string  | null   | 标识,选中时候触发 checkboxgroup 的 change 事件,并且携带 checkbox 的 value |
| disabled | boolean | False  | 是否禁用                                                                  |
| checked  | boolean | False  | 当前是否选中,可用来设置默认选中                                           |
| color    | Color   | null   | checkbox 的颜色,同 css 的 color                                           |

```javascript
<checkbox-group bindchange="checkboxChange">
  <checkbox value="USA" />
  美国
  <checkbox value="CHN" checked="true" />
  中国
  <checkbox value="BRA" />
  巴西
  <checkbox value="JPN" />
  日本
  <checkbox value="ENG" disabled /> 英国
</checkbox-group>;

//最后的值应该就是 ["CHN",'USA'],选中哪个就添加哪个
Page({
  checkboxChange(e) {
    console.log(e.detail.value);
  },
});
```

## radio 单项选择器

- radio 单项选择器 radio-group 由多个 radio 组成

| 属性     | 类型    | 默认值 | 说明                                                           |
| -------- | ------- | ------ | -------------------------------------------------------------- |
| value    | string  | null   | 标识,选中时候触发 radio 的 change 事件,并且携带 radio 的 value |
| disabled | boolean | False  | 是否禁用                                                       |
| checked  | boolean | False  | 当前是否选中,可用来设置默认选中                                |
| color    | Color   | null   | radio 的颜色,同 css 的 color                                   |

```javascript
<radio-group bindchange="radioChange">
  <radio value="USA" />
  美国
  <radio value="CHN" checked="true" />
  中国
  <radio value="BRA" />
  巴西
  <radio value="JPN" />
  日本
  <radio value="ENG" disabled /> 英国
</radio-group>;

//最后的值应该就是 ["CHN",'USA'],选中哪个就添加哪个
Page({
  radioChange(e) {
    console.log(e.detail.value);
  },
});
```

## input 单行输入框组件

| 属性     | 类型    | 默认值 | 说明             |
| -------- | ------- | ------ | ---------------- |
| value    | string  | null   | 输入框的初始内容 |
| type     | string  | text   | input 类型       |
| password | boolean | False  | 是否是密码类型   |

```javascript
<input type="text" bindinput="bindKeyInput">
```

## textarea 多行输入框

- 同单行输入框

## label 改进表单可用性(用处少)

- 他只有一个属性 for 用来绑定 id

## picker 滚动选择器

- 时间

- 普通

- 日期

### 普通选择器

| 属性       | 类型              | 默认值 | 说明                                                                                    |
| ---------- | ----------------- | ------ | --------------------------------------------------------------------------------------- |
| range      | array/Objectarray | []     | mode 为 selector 时,range 有效                                                          |
| range-key  | B2                | C2     | 当 range 是一个 object array 通过 range-key 来指定 object 中 key 的值作为选择器显示内容 |
| value      | number            | 0      | value 的值表示选择了 range 中的第几个(下标从 0 开始)                                    |
| bindchange | event             | null   | value 改变时候触发 change 事件 e.detail = value"value                                   |

- 代码

```bash

<picker bindchange="bindPickerChange" value="{{index}}" range="{{array}}">
 <view>
 当前选择 {{array[index]}}
 </view>
</picker>

-----JS部分--------
data:{
  array:["美国",'中国','巴西','日本'],
  index:0,
  objectArray:[
    {
      id:0,
      name:"美国"
    },
    {
      id:1,
      name:"中国"
    },
    {
      id:2,
      name:"巴西"
    },
    {
      id:3,
      name:"日本"
    }
  ]
}
bindPickerChange:function(e){
  console.log(e.detail.value)
  this.setData({
    index:e.detail.value
  })
}

```

## slider 滑动选择器

- 代码

```javascript
<slider bindchange="sliderchange" min="50" max="200" show-value/>
<slider bindchange="sliderchange" color="black" select-color="red"/>
```

## 开关选择器

- 用于性别之类的

| 属性       | 类型    | 默认值  | 说明                                                     |
| ---------- | ------- | ------- | -------------------------------------------------------- |
| checked    | boolean | False   | 是否选中                                                 |
| type       | string  | switch  | 样式 有效值,switch,checkbox                              |
| disabled   | boolean | False   | checked 改变时候触发 change 事件 e.detail= value:checked |
| color      | string  | #04BE02 | switch 的颜色同 css 的 color                             |
| bindchange | e       | null    | checked 改变触发 change,e.detail={value:checked}         |

```javascript
<switch type="switch" />
```

## form 表单提交

获取所有表单里面的值

- bindsubmit 携带 form 中的数据触发 submit 事件 e.detail = {value:{xxx}}

- bindreset 表单重置时触发 reset 事件

```html

<form bindsubmit="formSubmit" bindreset="formReset">
<slider name="silder"/>
<input type="text" name="user">
<radio-group name="radio-group">
<radio value="usa">美国
  </radio-group>
<button formType="submit">Submit</button>
<button formType="reset">Reset</button>
<form>

--------------

Page({
  formSubmit:function(){
    console.log(e.detail.value)
  },
  formReset:function(){
    console.log('发生了reset事件')
  }
})
```

## editor 富文本编辑器

- 代码

```html
<editor
  id="editor"
  bindready="onEditorReady"
  bindinput="onContentChange"
></editor>
```
