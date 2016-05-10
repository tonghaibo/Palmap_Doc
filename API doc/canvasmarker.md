 # NGR.CanvasMarker

CanvasMarker是一个基于Canvas的高性能Marker实现。不支持拖动，支持旋转，以米为单位固定大小，以及部分鼠标事件。当您需要向地图中添加超过30个以上的Marker时，建议使用CanvasMarker以提高性能。

## 简单用例
```javascript
NGR.canvasmarker([31.1, 121.1]).addTo(map);
```

## 创建方法
| 方法 | 描述 |
| -- | -- |
| `NGR.canvasmarker( <LatLng> latlng, <CanvasMarker options> options? >` | 使用给定的地理坐标和选项创建一个CanvasMarker |

## 选项
| 选项 | 类型 | 默认值 | 描述 |
| -- | -- | -- | -- |
| `icon` | `NGR.Icon` | * | 一个`NGR.Icon`的实例，可以参考其文档获取更多信息。在没有被指定的情况下，将使用`NGR.Icon.Default()`作为默认值 |
| `clickable` | `Boolean` | `false` | 如果设置为`true`，CanvasMarker将会响应鼠标的点击事件 |
| `opacity` | `Number` | `1` | 设置CanvasMarker的透明度 |
| `rotate` | `Number` | `0` | 以弧度为单位的顺时针旋转角度 |
| `fixedSize` | `Object` | `null` | 在地图渲染完成后固定CanvasMarker大小，并随地图缩放一起缩放。该选项的值是一个对象，形如：`{"icon": ["1m", "1m"], "shadow": ["80px", "80px"]}`，其中的`icon`和`shadow`分别与`icon`中指定的图标与阴影相对应，其值接收米`m`和像素`px`两种单位，在同一个数组中两种单位不能混用 |

## 方法
| 方法 | 返回值 | 描述 |
| -- | -- | -- |
| `addTo( <Map> map )` | `this`| 将CanvasMarker添加到map中 |
| `redraw()` | `this` | 强制重绘CanvasMarker |
| `getLatLng()` | `LatLng` | 获取当前CanvasMarker所在的地理位置 |
| `setLatLng( <LatLng> latlng )` | `this` | 为CanvasMarker设置新的地理位置 |
| `setFixedSize( <Object> size )` | `this` | 为CanvasMarker设置固定大小，参数形同`fixedSize`选项 |
| `setStyle( <Object> style )` | `this` | 为CanvasMarker设置参数，`style`支持选项中的所有字段。 |
