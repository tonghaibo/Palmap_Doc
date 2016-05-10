# NGR.Circle
一个用来在地图上显示圆的类，继承自`NGR.Path`。您可以使用`NGR.View`的`addLayer`方法将其添加到地图中去。

## 简单用法
```javascript
NGR.circle([31, 121], 200).addTo(map);
```

## 创建方法
| 创建方法 | 描述 |
| -- | -- |
| `NGR.circle( <LatLng> latlng, <Number> radius, <Path options> options? )` | 通过给定的地理坐标和半径在地图上创建一个圆 |

## 选项
该类的选项与 `NGR.Path` 中的选项相同

## 方法
| 方法 | 返回值 | 描述 |
| -- | -- | -- |
| `getLatLng()` | `LatLng` | 获取圆心的地理坐标 |
| `getRadius()` | `Number` | 获取以米为单位的圆形的半径 |
| `setLatLng( <LatLng> latlng )` | `this` | 为圆形设置新的圆心坐标 |
| `setRadius( <Number> radius )` | `this` | 为圆形设置新的以米为单位的半径 |
