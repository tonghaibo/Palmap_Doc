# NGR.DivIcon
`NGR.DivIcon`是一个使用`div`替代图片的轻量级图标类

## 简单用例
```javascript
var icon = NGR.divIcon({ className: 'palmap-predefined' });
// 可以在CSS中为palmap-predefined类添加样式
NGR.marker([31, 121], { icon: icon }).addTo(map);
```
默认情况下，`DivIcon`会带有一个名为`ngr-div-icon`的类，该类默认提供了一些边框阴影。

## 创建方法
| 创建方法 | 描述 |
| -- | -- |
| `NGR.divIcon( <DivIcon options> options )` | 通过给定的选项创建一个`DivIcon` |

## 选项
| 选项 | 类型 | 描述 |
| -- | -- | -- |
| `iconSize` | `Point` | 以像素为单位的Icon大小，也可以在CSS中进行设定 |
| `iconAnchor` | `Point` | 以像素为单位的Icon的锚点（相对于左上角） |
| `popupAnchor` | `Point` | 以像素为单位的弹出气泡的锚点 |
| `className` | `String` | 为`DivIcon`指定类名，覆盖默认的`ngr-div-icon`类 |
| `html` | `String` | 置于`div`中的一段HTML内容，默认为空 |
