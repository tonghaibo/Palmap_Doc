# NGR.Popup

Popup被用来在地图上的某个特定点打开一个气泡。您可以使用`map.openPopup()`以单例模式（只允许一个弹出气泡）打开一个气泡，或使用`map.addLayer()`添加多个气泡。

## 用法用例
如果您只想在Marker点击时打开一个气泡，只需执行这行代码：
```javascript
marker.bindPopup(popupContent).openPopup();
```
也可以用略微复杂点的方法：
```javascript
var popup = NGR.popup()
    .setLatLng(latlng)
    .setContent('<p>Hello World</p>')
    .openOn(map);
```

## 创建方法
| 创建方法 | 描述 |
| -- | -- |
| `NGR.Popup( <Popup options> options?, <ILayer> source? )` | 通过可选的选项和图层关系创建弹出气泡.其中选项用来指定弹出气泡的样式，图层关系用来将气泡和图层联系起来 |

## 选项
| 选项 | 类型 | 默认值 | 描述 |
| -- | -- | -- | -- |
| `maxWidth` | `Number` | `300` | 弹出气泡的最大宽度 |
| `minWidth` | `Number` | `50` | 弹出气泡的最小宽度 |
| `maxHeight` | `Number` | `null` | 如果设置了此值，将为超高的内容创建一个可卷动的容器 |
| `keepInView` | `Boolean` | `false` | 如果您想阻止用户在弹出气泡被打开时将气泡移出视野外，可以将其设置为`true` |
| `closeButton` | `Boolean` | `true` | 在气泡中提供默认的关闭按钮 |
| `closeOnClick` | `Boolean` | `null` | 如果您想阻止在点击地图其他区域时自动关闭弹出气泡，请将其设置为`false` |
| `className` | `String` | `''` | 为弹出窗口元素指定一个自定义DOM类名 |

## 方法
| 方法 | 返回值 | 描述 |
| -- | -- | -- |
| `addTo( <Map> map )` | `this` | 将气泡添加到地图中 |
| `openOn( <Map> map )` | `this` | 与`Map`的`openPopup()`方法相同，尽在屏幕上保留一个气泡 |
| `setLatLng( <LatLng> latlng )` | `this` | 设定气泡打开时的地理位置 |
| `getLatLng()` | `LatLng` | 返回气泡所在的地理位置 |
| `setContent(< String or HTMLElement> htmlContent )` | `this` | 为气泡设置HTML内容 |
| `getContent()` | `<String or HTMLElement>` | 获取气泡的内容 |
| `update()` | `this` | 强制更新气泡的内容、布局与位置。 |
