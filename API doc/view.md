NGR.View
=========

NGR.View 是室内地图 API 的核心部分，它会被用来在页面上创建室内地图并维护其的状态。

简单用例
--------
```javascript
var map = NGR.view('map', {
    center: [31, 121],
    zoom: 21
});
```

创建地图
--------
| **方法** | **描述** |
| ----------- | --------------- |
|<code>NGR.view(&lt;HTMLElement&#124;String&gt; id, &lt;Map Options&gt; options?)</code>| 在指定的元素上初始化室内地图，id可以是一个HTMLElement，也可以是某个元素的id。在初始化时，可以指定一些可选的选项。|

### 选项
#### 与授权相关的选项
| 选项 | 类型 | 默认值 | 描述 |
| -- | -- | -- | -- |
| `AppKey` | `String` | `null` | 由开放平台分配的AppKey |

#### 与地图状态相关的选项
| 选项 | 类型 | 默认值 | 描述 |
| ---- | ---- | ------ | ---- |
| `center` | `LatLng` | `null` | 为地图指定初始化时的中心点 |
| `zoom`   | `Number` | `null` |为地图指定初始化时的缩放比例 |
| `layers` | `ILayer` | `null` |为地图指定初始化时要添加的图层 |
| `minZoom` | `Number` | `null` | 地图上允许的最小缩放比例，该设置将覆盖任意图层的`minZoom`设置 |
| `maxZoom` | `Number` | `null` | 地图上允许的最大缩放比例，该设置将覆盖任意图层的`maxZoom`设置 |
| `maxBounds` | `LatLngBounds` | `null` | 在设置了这个选项之后，地图会将视图区域限制在给定的地理范围中。可以使用`setMaxBounds`方法来动态改变限制区域的大小 |

#### 与交互相关的选项
| 选项 | 类型 | 默认值 | 描述 |
| -- | -- | -- | -- |
| `dragging` | `Boolean` | `true` | 指定地图是否能够被拖动 |
| `touchZoom` | `Boolean` | `true` | 指定地图是否允许双指缩放 |
| `scrollWheelZoom` | `Boolean` | `true` | 指定地图是否能够通过鼠标滚轮进行缩放。如果将值设置为 `center`， 地图将会忽略鼠标当前的位置，以屏幕中心点为中心进行缩放 |
| `doubleClickZoom` | `Boolean` | `true` | 指定地图是否能够通过双击进行放大，按住 `shift` 双击进行缩小。如果将值是指为 `center`，地图将会忽略当前鼠标的位置，以屏幕中心点为中心进行缩放 |
| `boxZoom` | `Boolean` | `true` | 指定是否启用通过按住 `Shift` 在地图上拖动画出矩形进行放大。 |
| `closePopupOnClick` | `Boolean` | `true` | 如果不想在用户单击地图时关闭弹出气泡，可以设置为 `false` |

#### 与键盘导航相关的选项
| 选项 | 类型 | 默认值 | 描述 |
| -- | -- | -- | -- |
| `keyboard` | `Boolean` | `true` | 此选项可以使地图能够获取焦点并允许用户使用键盘的方向键和+/-号进行导航 |
| `keyboardPanOffset` | `Number` | 80 | 指定当使用键盘方向键移动地图时每次平移的像素数 |
| `keyboardZoomOffset` | `Number` | 1 | 指定当使用+/-号缩放地图时每次缩放的级数 |

#### 与控件相关的选项

| 选项 | 类型 | 默认值 | 描述 |
| -- | -- | -- | -- |
| `zoomControl` | `Boolean` | `true` | 指定是否默认加载地图缩放控件 |

### 事件
您可以通过这些方法来订阅下列事件。

| 事件 | 数据类型 | 描述 |
| -- | -- | -- |
| `click` | `MouseEvent` | 当用户点击或点触地图时触发 |
| `dblclick` | `MouseEvent` | 当用户双击或两次快速点触地图时触发 |
| `mousedown` | `MouseEvent` | 当用户在地图上按下鼠标按键时触发 |
| `mouseup` | `MouseEvent` | 当用户在地图上释放鼠标按键时触发 |
| `mouseover` | `MouseEvent` | 当鼠标指针进入地图时触发 |
| `mouseout` | `MouseEvent` | 当鼠标指针移出地图时触发 |
| `mousemove` | `MouseEvent` | 当鼠标指针在地图上时触发 |
| `contextmenu` | `MouseEvent` | 当用户在地图上按下鼠标右键时触发，如果为本事件添加监听器，将会禁用默认的浏览器上下文菜单。该事件也会在长按地图时被触发 |
| `focus` | `Event` | 当地图通过点击或Tab获取焦点时被触发 |
| `blur` | `Event` | 当地图失去焦点时被触发 |
| `preclick` | `MouseEvent` | 在地图上的鼠标事件触发前被触发 |
| `load` | `Event` | 当地图初始化（即第一次设置中心点和缩放比例）完成后被触发 |
| `unload` | `Event` | 当地图通过 `remove` 方法被销毁时触发 |
| `viewreset` | `Event` | 当地图需要重绘内容时被触发（通常发生在地图缩放或加载时），在创建自定义图层时很有用 |
| `movestart` | `Event` | 当地图视野开始改变时触发（例如当用户开始拖拽地图时） |
| `move` | `Event` | 当地图视野被移动时触发 |
| `moveend` | `Event` | 当地图视野改变完成后触发（例如当用户停止拖拽地图时） |
| `dragstart` | `Event` | 当用户开始拖拽地图时触发 |
| `drag` | `Event` | 当用户拖拽地图时触发 |
| `dragend` | `DragEndEvent` | 当用户停止拖拽地图时触发 |
| `zoomstart` | `Event` | 当地图缩放层级将要被改变时触发（例如在缩放动画前触发） |
| `zoomend` | `Event` | 当地图缩放层级改变后被触发 |
| `zoomlevelschange` | `Event` | 当地图的缩放层级因为添加/移出图层而改变 |
| `resize` | `ResizeEvent` | 当地图大小发生改变时被触发 |
| `autopanstart` | `Event` | 当地图因为打开气泡而自动调整位置时被触发 |
| `layeradd` | `LayerEvent` | 当添加一个或多个新的图层时被触发 |
| `layerremove` | `LayerEvent` | 当移除一个或多个现有的图层时被触发 |
| `popupopen` | `PopupEvent` | 当使用 `openPopup` 方法打开一个弹出气泡时被触发 |
| `popupclose` | `PopupEvent` | 当使用 `closePopup` 方法关闭一个弹出气泡时被触发 |

### 与修改地图状态相关的方法
| 方法 | 返回类型 | 描述 |
| -- | -- | -- |
| `setView( <LatLng> center, <Number> zoom?, <zoom/pan options> options? )` | `this` | 为地图设置显示区域（地理中心位置和缩放等级）并给定动画选项 |
| `setZoom( <Number> zoom, <zoom options> options? )` | `this` | 为地图设置缩放等级 |
| `zoomIn( <Number> delta?, <zoom options> options? )` | `this` | 增加 `delta` 个缩放等级，默认为1 |
| `zoomOut( <Number> delta?, <zoom options> options? )` | `this` | 减少 `delta` 个缩放等级，默认为1 |
| `setZoomAround( <LatLng> latlng, <Number> zoom, <zoom options> options? )` | `this` | 以特定点为中心将地图缩放到指定的缩放等级 |
| `fitBounds( <LatLngBounds> bounds, <fitBounds options> options? )` | `this` | 尽可能地将地图缩放到给定地理范围的大小 |
| `panTo( <LatLng> latlng, <pan options> options? )` | `this` | 将地图中心点移动至特定位置 |
| `panInsideBounds( <LatLngBounds> bounds, <pan options> options? )` | `this` |  移动地图，使其尽可能包含给定的地理范围 |
| `panBy( <Point> point, <pan options> options? )` | `this` | 依据给定的像素移动地图 |
| `setMaxBounds( <LatLngBounds> bounds )` | `this` | 设置地图可显示的最大地理范围 |
| `setMinZoom()` | `this` | 设置地图允许的最小缩放层级 |
| `setMaxZoom()` | `this` | 设置地图允许的最大缩放层级 |
| `remove()` | `this` | 销毁地图并清空所有的事件监听器 |

### 与获取地图状态相关的方法
| 方法 | 返回类型 | 描述 |
| -- | -- | -- |
| `getCenter()` | `LatLng` | 返回地图当前视野的地理中心点 |
| `getZoom()` | `Number` | 返回地图当前视野的缩放层级 |
| `getMinZoom()` | `Number` | 返回地图允许的最小缩放层级 |
| `getMaxZoom()` | `Number` | 返回地图允许的最大缩放层级|
| `getBounds()` | `LatLngBounds` | 返回地图当前视野的地理区域 |
| `getBoundsZoom( <LatLngBounds> bounds, <Boolean> inside?)` | `Number` | 返回能被给定地理区域范围包含的最大缩放等级，如果 `inside`（可选） 被指定为 `true`，则返回能包含给定地理区域范围的最小缩放等级 |
| `getSize()` | `this` | 返回当前地图容器的大小 |
| `getContainer()` | `HTMLElement` | 返回当前地图所在的容器 |

### 与图层和控件相关的方法
| 方法 | 返回类型 | 描述 |
| -- | -- | -- |
| `addLayer( <ILayer> layer )` | `this` | 向地图中添加给定的图层 |
| `removeLayer( <ILayer> layer )` | `this` | 从地图中移除给定的图层 |
| `hasLayer( <ILayer> layer )` | `Boolean` | 如果给定的图层已经被添加到了地图中，则返回 `true` |
| `eachLayer( <Function> fn, <Object> context? )` | `this` | 遍历室内地图中的所有图层，可以为遍历函数指定一个可选的上下文环境 |
| `openPopup( <Popup> popup )` | `this` | 关闭地图上所有现存的气泡并打开一个新的气泡 |
| <code>openPopup( &lt;String&gt; html &#124; &lt;HTMLElement&gt; el, &lt;LatLng&gt; latlng, &lt;Popup options&gt; options? )</code> | `this` | 使用特定的选项配置并在地图上的特定位置打开弹出气泡 |
| `closePopup( <Popup> popup? )` | `this` | 关闭所有使用 `openPopup` 打开的气泡，或指定一个要关闭的气泡 |
| `addControl( <IControl> control )` | `this` | 添加一个指定的地图控件 |
| `removeControl( <IControl> control )` | `this` | 移除指定的地图控件 |

### 与坐标转换相关的方法
| 方法 | 返回类型 | 描述 |
| -- | -- | -- |
| `latLngToContainerPoint( <LatLng> latlng )` | `Point` | 返回与给定地理坐标相对应的地图容器坐标点（以像素为单位） |
| `containerPointToLatLng( <Point> point )` | `LatLng` | 返回与给定屏幕容器坐标相对应的地理坐标点 |
| `mouseEventToContainerPoint( <MouseEvent> event )` | `Point` | 返回鼠标事件相对于地图容器的像素坐标点 |
| `mouseEventToLatLng( <MouseEvent> event )` | `LatLng` | 返回鼠标事件对应的地理坐标点 |

### 与渲染相关的方法
| 方法 | 返回类型 | 描述 |
| -- | -- | -- |
| `render()` | `this` | 将地图缩放到合适的大小并渲染地图 |
| `clear()` | `this` | 清空所有的图层 |
