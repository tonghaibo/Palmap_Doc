# NGR.Polyline
一个可以在地图上画出折线的类，继承自`NGR.Path`。您可以使用`NGR.View`的`addLayer`方法将其添加到地图中去。

## 简单用例
```javascript
// 根据给定的地理坐标序列创建一个红色的折线
var polyline = NGR.polyline(latlngs, { color: 'red' }).addTo(map);
// 将地图缩放到适应折线的缩放比例
map.fitBounds(polyline.getBounds());
```

## 创建方法
| 创建方法 | 描述 |
| -- | -- |
| `NGR.polyline( <LatLng[]> latlngs, <Polyline options> options? )` | 通过给定的地理坐标序列和选项创建一个折线类 |


## 选项
该类的选项与 `NGR.Path` 中的选项相同

## 方法
除了可以使用 `NGR.Path` 中所提供的方法以外，还可以使用下列方法：

| 方法 | 返回值 | 描述 |
| -- | -- | -- |
| `addLatLng( <LatLng> latlng )` | `this` | 向折线末端添加一个新的地理坐标点 |
| `setLatLngs( <LatLng[]> latlngs) ` | `this` | 重设组成折线的地理坐标点组 |
| `getLatLngs()` | `LatLng[]` | 获取组成折线的地理坐标点组 |
| `spliceLatLngs( <Number> index, <Number> pointsToRemove, <LatLng> latlng?, ... )` | `LatLng[]` | 修改地理坐标点组，与[Array的splice方法](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Array/splice)用法相同 |
| `getBounds()` | `LatLngBounds` | 获取折线的最小地理围栏大小 |