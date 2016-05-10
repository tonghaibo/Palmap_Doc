# NGR.Icon
代表创建Marker时要用到的图标

## 简单用例
```javascript
var icon = NGR.icon({
    iconUrl: 'path/to/icon.png',
    iconSize: [100, 100],
    iconAnchor: [30, 30],
    popupAnchor: [70, 70],
    shadowUrl: 'path/to/shadow.png',
    shadowSize: [90, 60],
    shadowAnchor: [30, 20]
});

NGR.marker([31, 121], { icon: icon}).addTo(map);
```
`NGR.Icon.Deafult`是一个继承自`NGR.Icon`的默认图标，默认情况下SDK将会使用这个图标。

## 创建方法
| 创建方法 | 描述 |
| -- | -- |
| `NGR.icon( <Icon options> options )` | 通过给定的选项创建图标 |

## 选项
| 选项 | 类型 | 描述 |
| -- | -- | -- |
| `iconUrl` | `String` | 图标的Url（相对于脚本文件的路径） |
| `iconSize` | `Point` | 以像素为单位的Icon的大小 |
| `iconAnchor` | `Point` | 图标的锚点（相对于图标的左上角）。在将Marker放置到一个指定的地理位置上时，图标的锚点会与这个地理位置重合。如果没有指定，将默认为图标的中心点 |
| `shadowUrl` | `String` | 图标阴影部分的Url。指定阴影可以产生3D效果。如果不指定，则不会附带阴影 |
| `shadowSize` | `Point` | 以像素为单位的阴影的大小 |
| `shadowAnchor` | `Point` | 阴影的锚点 |
| `popupAnchor` | `Point` | 弹出气泡的锚点 |
