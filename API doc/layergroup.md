# NGR.LayerGroup
`LayerGroup`可以将多个图层归为一组，您可以将这个组添加到地图中去。添加后任何对组的操作都将反映在地图上。

## 简单用例
```javascript
NGR.layerGroup([marker1, marker2]).addLayer(marker3).addTo(map);
```

## 创建方法
| 方法 | 描述 |
| -- | -- |
| `NGR.layerGroup( <ILayer[]> layers? )` | 创建一个新的LayerGroup |

## 方法
| 方法 | 返回值 | 描述 |
| -- | -- | -- |
| `addTo( <Map> map )` | `this` | 向地图中添加图层组 |
| `addLayer( <ILayer> layer )` | `this` | 将指定图层添加到图层组中 |
| `removeLayer( <ILayer> layer )` | `this` | 从图层组中移除指定图层 |
| `removeLayer( <String> id )` | `this` | 从图层组中移除指定编号的图层 |
| `hasLayer( <ILayer> layer )` | `Boolean` | 查询图层组中是否包含指定的图层 |
| `getLayer( <String> id )` | `NGR.ILayer` | 从图层组中获取指定图层 |
| `getLayers()` | `Array` | 获取图层组中的所有图层 |
| `clearLayers()` | `this` | 清除图层组中的所有图层 |
| `eachLayer( <Function> fn, <Object> context? )` | `this` | 遍历图层组中的所有图层，可以通过`context`为遍历函数指定`this` |
