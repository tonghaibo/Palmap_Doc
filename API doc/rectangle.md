# NGR.Rectangle
一个可以在地图上画出矩形的类，继承自`NGR.Polygon`。您可以使用 `NGR.View` 的 `addLayer` 方法将其添加到地图中去。

## 用法用例
```javascript
//定义一个矩形地理边框
var bounds = [[31, 121], [32, 122]];

// 创建一个红色的矩形
NGR.rectangle(bounds, {color: 'red', weight: 1}).addTo(map);

// 将地图缩放到矩形区域
map.fitBounds(bounds);
```

## 创建方法
| 创建方法 | 描述 |
| -- | -- |
| `NGR.rectangle( <LatLngBounds> bounds, <Path options> options? )` | 使用给定的地理围栏和选项（与`NGR.Path`的选项一致）创建一个新的矩形图形对象 |

## 方法
除了可以使用 `NGR.Path` 中所提供的方法以外，还可以使用下列方法：

| 方法 | 返回值 | 描述 |
| -- | -- | -- |
| `setBounds( <LatLngBounds> bounds )` | `this` | 使用给定的地理围栏重绘矩形 |

