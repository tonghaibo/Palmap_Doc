# NGR.Polygon
一个可以在地图上画出多边形的类。继承自`NGR.Polyline`。您可以使用`NGR.View`的`addLayer`方法将其添加到地图中去。

**注意**：您用来创建多边形的点集中第一个点和最后一个点不应该重叠，我们建议您在创建前过滤掉这些点。

## 创建方法
| 创建方法 | 描述 |
| -- | -- |
| `NGR.polygon( <LatLng[]> latlngs, <Path options> options? )` | 使用给定的地理坐标点数组和选项（与`NGR.Path`的选项相同）创建多边形 |

## 方法
除了可以使用 `NGR.Path` 中所提供的方法以外，还可以使用下列方法：

| 方法 | 返回值 | 描述 |
| -- | -- | -- |
| `getCentroid()` | `LatLng` | 返回多边形的重心 |
| `getInnerPoint()` | `LatLng` | 返回一个在多边形内的点 |
