# 地图组件

- 标记点

- 轨迹点

- 显示控件

## 标记点

```javascript
markers: [
  {
    iconPath: 'xxxxx',
    id: 0,
    latitude: 23.0009994,
    longitude: 113.32452,
    width: 50,
    height: 50,
  },
];
```

## polyline

- 轨迹

```javascript
polyline: [
  {
    points: [
      {
        longitude: 23.0003,
        latitude: 23.10229,
      },
      {
        longitude: 113.324553,
        latitude: 23.21229,
      },
    ],
    color: '#FF0000DD',
    width: 2,
    dottedLine: true,
  },
];
```

## 显示控件

```javascript
controls: [
  {
    id: 1,
    iconPath: '/images/control.png',
    position: {
      left: 0,
      top: 500 - 50,
      width: 50,
      height: 50,
    },
    clickable: true,
  },
];
```

## 属性说明

| 属性      | 类型   | 默认值 | 说明     |
| --------- | ------ | ------ | -------- |
| longitude | number | null   | 经度     |
| latitude  | number | null   | 纬度     |
| scale     | number | 16     | 缩放级别 |

剩下的请看文档
