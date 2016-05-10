# NGR.CircleMarker
一个以像素为单位固定半径的圆。继承自`NGR.Circle`。您可以使用`NGR.View`的`addLayer`方法将其添加到地图中去。

## 创建方法
| 创建方法 | 描述 |
| -- | -- |
| `NGR.circleMarker( <LatLng> latlng, <Path options> options? )` | 根据给定的地理位置坐标和以米为单位的可选的半径创建一个CircleMarker图层，默认半径为`10m`，您可以在`options`中新增一个字段`radius`来手工指定这个值 |

## 方法
与`NGR.Circle`的方法一致
