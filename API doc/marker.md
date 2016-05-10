# NGR.Marker

用来向地图中添加一个标记（Marker），例如：

`NGR.marker([31.1, 121.1]).addTo(map);`

## 创建方法
| 创建方法 | 描述 |
| -- | -- |
| `NGR.marker( <LatLng> latlng, <Marker options> options? )` | 使用给定的地理坐标和选项创建并实例化一个标记 |

## 选项
| 选项 | 类型 | 默认值 | 描述 |
| -- | -- | -- | -- |
| `icon` | `NGR.Icon` | * | 用来渲染Marker的图标。可以查看`NGR.Icon`的文档来获取更多的相关文档，如果没有指定，则默认为`NGR.Icon.Deafult()` |
| `clickable` | `Boolean` | `true` | 如果设为`false`，Marker将不会响应任何鼠标事件 |
| `draggable` | `Boolean` | `false` | 配置Marker是否能被鼠标或触摸拖动 |
| `keyboard` | `Boolean` | `true` | 配置Marker是否可以通过`tab`获取焦点并通过`Enter`点击 |
| `title` | `String` | `''` | 配置当鼠标覆盖在Marker上时浏览器显示的`tooltip`文本 |
| `alt` | `String` | `''` | 配置Marker图标元素的`alt`属性文本 |
| `zIndexOffset` | `Number` | `0` | 默认情况下，Marker图标的`zIndex`属性是基于地理位置自动设置的。使用这个选项可以强制指定`zIndex`属性将图标置于顶层 |
| `opacity` | `Number` | `1.0` | Marker的透明度 |
| `riseOnHover` | `Boolean` | `false` | 如果被设为`true`，Marker会在被鼠标覆盖时移至最上方 |
| `riseOffset` | `Number` | `250` | `riseOnHover`属性要使用的`zIndex`值 |

## 事件
| 事件 | 数据 | 描述 |
| -- | -- | -- |
| `click` | `MouseEvent` | 当用户点击或触摸Marker时被触发 |
| `dblclick` | `MouseEvent` | 当用户双击或两次快速点击Marker时被触发 |
| `mousedown` | `MouseEvent` | 当用户在Marker上按下鼠标时被触发 |
| `mouseover` | `MouseEvent` | 当鼠标指针进入Marker时被触发 |
| `mouseout` | `MouseEvent` | 当鼠标指针移出Marker时被触发 |
| `contextmenu` | `MouseEvent` | 当用户右击Marker时被触发 |
| `dragstart` | `Event` | 当用户开始拖拽Marker时被触发 |
| `drag` | `Event` | 在用户拖拽Marker时持续触发 |
| `dragend` | `DragEndEvent` | 当用户停止拖拽Marker时被触发 |
| `move` | `Event` | 当Marker通过`setLatLng`方法被移动时触发，新的坐标会被包含在事件参数中 |
| `add` | `Event` | 当Marker添加到地图上时被触发 |
| `remove` | `Event` | 当Marker从地图上移除时被触发 |
| `popupopen` | `PopupEvent` | 当绑定在Marker上的弹出气泡打开时被触发 |
| `popupclose` | `PopupEvent` | 当绑定在Marker上的弹出气泡关闭时被触发 |


## 方法
| 方法 | 返回值 | 描述 |
| -- | -- | -- |
| `addTo( <Map> map )` | `this` | 将Marker添加到地图中 |
| `getLatLng()` | `LatLng` | 返回Marker所在的地理位置 |
| `setLatLng( <LatLng> latlng )` | `this` | 将Marker的位置变更到给出的地理坐标点上 |
| `setIcon( <Icon> icon )` | `this` | 改变Marker的图标 |
| `setZIndexOffset( <Number> offset )` | `this` | 改变Marker的`zIndex`属性值 |
| `setOpacity( <Number> opacity )` | `this` | 改变Marker的透明度 |
| `update()` | `this` | 更新Marker的位置，在`latlng`属性被直接改变时需要强制更新 |
| <code>bindPopup( &lt;String&gt; html &#124; &lt;HTMLElement&gt; el &#124; &lt;Popup&gt; popup, &lt;Popup options&gt; options? ) </code> | `this` | 为Marker绑定一个弹出气泡，当点击Marker时会弹出这个气泡。您也可以通过调用`openPopup()`以编程的方式打开气泡 |
| `unbindPopup()` | `this` | 解除Marker对弹出气泡的绑定 |
| `openPopup()` | `this` | 打开通过`bindPopup`绑定的气泡 |
| `getPopup()` | `Popup` | 返回通过`bindPopup`绑定的气泡 |
| `closePopup()` | `this` | 关闭被绑定的气泡 |
| `togglePopup()` | `this` | 切换被绑定的气泡的状态 |
| <code>setPopupContent( &lt;String&gt; html &#124; &lt;HTMLElement&gt; el ) </code> | `this` | 为Marker绑定的气泡设置HTML内容 |


## 交互处理器
交互处理器是Marker实例的一个属性，可以通过它在运行时改变交互行为，启用或关闭诸如拖动之类的操作。例如：
`marker.dragging.disable()`
