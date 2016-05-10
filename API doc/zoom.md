# NGR.Control.Zoom
仅带有放大缩小功能的基本的缩放控件。除非地图的`zoomControl`被设为`false`，否则地图会默认启用此控件。此控件继承自`NGR.Control`。

## 创建方法
| 创建方法 | 描述 |
| -- | -- |
| `NGR.control.zoom( <Control.Zoom options> options? )` | 创建一个缩放控件 |

## 选项
| 选项 | 类型 | 默认值 | 描述 |
| -- | -- | -- | -- |
| `position` | `String` | `topleft` | 控件的位置 |
| `zoomInText` | `String` | `+` | 放大按钮中的文字 |
| `zoomOutText` | `String` | `-` | 缩小按钮中的文字 |
| `zoomInTitle` | `String` | `Zoom in` | 放大按钮tip里的文字 |
| `zoomOutTitle` | `String` | `Zoom out` | 缩小按钮tip里的文字 |
