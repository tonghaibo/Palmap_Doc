# NGR.CanvasLabel

CanvasLabel是一个基于Canvas的高性能Label实现。可以用来向地图中添加文字内容。当需要向地图中添加超过30个以上的Label时，建议使用CanvasLabel以提高性能。

## 简单用例
```javascript
NGR.canvaslabel([31, 121], { textContent: 'hello' }).addTo(map);
```

## 创建方法
| 方法 | 描述 |
| -- | -- |
| `NGR.canvaslabel( <LatLng> latlng, <CanvasLabel options> options? >` | 使用给定的地理坐标和选项创建一个CanvasLabel |

## 选项
| 选项 | 类型 | 默认值 | 描述 |
| -- | -- | -- | -- |
| `stroke` | `Boolean` | `false` | 是否绘制文字的边框 |
| `color` | `String` | `#000` | 文字边框的颜色 |
| `opacity` | `Number` | `1` | 文字边框的透明度 |
| `fill` | `Boolean` | `true` | 是否填充文字 |
| `fillOpacity` | `Number` | `1` | 填充透明度 |
| `fillColor` | `String` | `#000` | 填充颜色 |
| `textAlign` | `String` | `center` | 文字对齐位置，参见[这篇文档](https://developer.mozilla.org/en-US/docs/Web/API/CanvasRenderingContext2D/textAlign)获取更多信息 |
| `textBaseline` | `String` | `middle` | 文字基线位置，参见[这篇文档](https://developer.mozilla.org/en-US/docs/Web/API/CanvasRenderingContext2D/textBaseline)获取更多信息 |
| `font` | `String` | `'13px/1.4 "Microsoft YaHei"...'` | 设置显示字体 |
| `textContent` | `String` | `null` | 标签内容 |
| `boundPolygon` | `NGR.Polygon` | `null` | 绑定多边形，绑定后当多边形缩小至不能容纳标签时，标签会自动隐藏 |

## 方法
| 方法 | 返回值 | 描述 |
| -- | -- | -- |
| `addTo( <Map> map )` | `this`| 将CanvasLabel添加到map中 |
| `redraw()` | `this` | 强制重绘CanvasLabel |
| `getLatLng()` | `LatLng` | 获取当前CanvasLabel所在的地理位置 |
| `setLatLng( <LatLng> latlng )` | `this` | 为CanvasLabel设置新的地理位置 |
| `getContent()` | `String` | 获取当前标签内的文字内容 |
| `setContent( String content )` | `this` | 为当前标签设置新的文字内容 |
| `setStyle( <Object> style )` | `this` | 为CanvasLabel重新设置参数，`style`支持选项中的所有字段。 |
