# 图层接口
**本文暂时不公开**

`ILayer`接口抽象自所有可以添加到地图指定位置上的对象。在SDK中，`Marker`、`Popup`、`LayerGroup`等均实现了本接口。

## 方法
| 方法 | 返回值 | 描述 |
| -- | -- | -- |
| `onAdd( <View> map)` | `-` | 在该方法中应该执行创建并添加DOM元素，配置监听器等操作。该方法将在`map.addLayer(layer)`时被调用 |
| `onRemove( <View> map )` | `-` | 在该方法中应该执行移除元素监听器等清理工作。该方法将在`map.removeLayer(layer)`时被调用 |

## 实现自定义图层
实现自定义图层中最重要的是要监听地图的`viewreset`事件和`latLngToLayer
