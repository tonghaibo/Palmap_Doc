# NGR.Path
这是一个抽象类，是所有基本图形（折线，多边形，圆形）的父类，封装了部分共同属性。


## 选项
| 选项 | 类型 | 默认值 | 描述 |
| -- | -- | -- | -- |
| `stroke` | `Boolean` | `true` | 选择是否绘制路径。设置为`false`可以为多边形和圆形禁用边框 |
| `color` | `String` | `'#03f'` | 绘制要使用的颜色 |
| `weight` | `Number` | `5` | 以像素为单位的绘制宽度 |
| `opacity` | `Number` | `0.5` | 设定绘制时的透明度 |
| `fill` | `Boolean` | 不确定 | 选择是否使用颜色填充路径。设置为`false`可以为多边形和圆形禁用填充 |
| `fillColor` | `String` | 与`color`相同 | 填充要使用的颜色 |
| `fillOpacity` | `Number` | `0.2` | 设置填充时的透明度 |
| `lineCap` | `String` | `null` | 一段用来[设置绘制线段末端图形的字符串](https://developer.mozilla.org/zh-CN/docs/Web/API/CanvasRenderingContext2D/lineCap) |
| `lineJoin` | `String` | `null` |一段用来[设置绘制线段相交图形的字符串](https://developer.mozilla.org/zh-CN/docs/Web/API/CanvasRenderingContext2D/lineJoin) |
| `clickable` | `Boolean` | `true` | 如果被设置为`false`，图形将不会响应鼠标事件 |

## 事件
您可以通过事件API来订阅下列事件：

| 事件 | 数据 | 描述 |
| -- | -- | -- |
| `click` | `MouseEvent` | 当用户点击或触摸该图形时被触发 |
| `dblclick` | `MouseEvent` | 当用户双击或两次触摸该图形时被触发 |
| `mousedown` | `MouseEvent` | 当用户在该图形上按下鼠标时被触发 |
| `mouseover` | `MouseEvent` | 当鼠标进入该图形时被触发 |
| `mouseout` | `MouseEvent` | 当鼠标移出该图形时被触发 |
| `contextmenu` | `MouseEvent` | 当用户在该图形上点击右键时被触发。如果监听了这个事件，将会阻止触发浏览器的默认事件 |
| `add` | `Event` | 当图形被添加到地图上时被触发 |
| `remove` | `Event` | 当图形被从地图上移除时被触发 |
| `popupopen` | `PopupEvent` | 当绑定在该图形上的弹出气泡打开时被触发 |
| `popupclose` | `PopupEvent` | 当绑定在该图形上的弹出气泡关闭时被触发 |

## 方法
| 方法 | 返回值 | 描述 |
| -- | -- | -- |
| `addTo( <Map> map )` | `this` | 将图形添加到地图中去 |
| `bindPopup( <String> html, <Popup Options> options? )` | `this` | 为该图形绑定一个指定内容的气泡，当点击时，气泡会被触发 |
| `bindPopup( <HTMLElement> el, <Popup Options> options? )` | `this` | 为该图形绑定一个指定内容的气泡，当点击时，气泡会被触发 |
| `bindPopup( <Popup> popup, <Popup Options> options? )` | `this` | 为该图形绑定一个指定内容的气泡，当点击时，气泡会被触发 |
| `unbindPopup()` | `this` | 解绑先前使用`bindPopup`函数绑定的气泡 |
| `openPopup( <LatLng> latlng? )` | `this` | 在指定的经纬度上打开弹出气泡，如不指定，则在路径上的任选一点打开气泡 |
| `closePopup()` | `this` | 关闭在图形上绑定的气泡 |
| `setStyle( <Path options> object )` | `this` | 为图形重新设置样式 |
| `getBounds()` | `this` | 获取图形的地理围栏边框 |
| `bringToFront()` | `this` | 将该图层置于所有图层之上 |
| `bringToBack()` | `this` | 将该图层置于所有图层之下 |
| `redraw()` | `this` | 强制重绘图层 |
