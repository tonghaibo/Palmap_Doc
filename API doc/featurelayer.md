# NGR.FeatureLayer
`NGR.FeatureLayer`可以解析由开放平台提供的数据，为其赋予样式并将其转换为地图图层。设定样式时，可以以编程的方式动态设定，也可以通过配置文件的方式进行设定。


## 用法用例
```javascript
NGR.featureLayer(data, {
    styleConfig: config
}).addTo(map);
```

## 创建方法
| 创建方法 | 描述 |
| -- | -- |
| `NGR.featureLayer( <Object> data, <Featurelayer options> options? )` | 根据给定的图层数据和选项创建地图图层 |


## 选项
| 选项 | 类型 | 描述 |
| -- | -- | -- | -- |
| `styleConfig` | `Object` | 样式配置对象 |
| `layer_type` | `String` | 显式指定图层类型，覆盖数据中携带的图层类型 |
| `pointToLayer` | `Function(feature, latlng)` | 指定地图数据中“点”数据类型的处理函数。该函数要求返回一个图层，如果没有指定，默认将“点”转换为Marker。函数的参数`feature`为开放平台提供的内容，`latlng`为点的地理坐标 |
| `style` | `Function(feature) or Object` | 指定地图数据的样式处理函数或样式内容。若提供一个函数，则要求返回一个包含渲染样式的`Object`；若提供的是一个`Object`，则直接包含渲染样式即可 |
| `onEachFeature` | `Function(feature, layer)` | 这个函数会在每个feature被创建时被调用。可以在这个函数里完成绑定事件之类的操作 |
| `filter` | `Function(feature, layer)` | 指定Feature是否要被渲染的函数，该函数的参数`feature`提供了Feature的详细信息，`layer`提供了转换为图层后的对象，函数须返回一个布尔值，决定该Feature是否要被渲染 |

## 方法
| 方法 | 返回值 | 描述 |
| -- | -- | -- |
| `addTo( <Map> map )` | `this` | 向`map`中添加本图层 |
| `addFeautre( <Feature> feature )` | `this` | 向本图层中添加新的feature |
| `removeFeature( <Feature> feature )` | `this` | 从本图层中移除一个已有的feature |
| `resetStyle( <ILayer> layer )` | `this` | 将样式重设为开放平台数据中预设的样式，用于手动改变样式后重置样式 |
| `getLayerByFeatureId( <String> featureId )` | `ILayer` | 通过feature的ID获取图层中的图形 |
| `getLabelByFeatureId( <String> featureId )` | `CanvasLabel` | 通过feature的ID获取图层中的label |
| `clearLayers()` | `this` | 清除图层中所有的图形 |
| `getBounds()` | `LatLngBounds` | 获取图层中所有元素组成的地理边界 |


## 通过配置文件加载样式
配置文件（即`options`中的`styleConfig`）是一段JSON内容，结构形如：
```json
{
    "layer_type": {
        "type": enum of "inherit", "Point", "MultiPoint", "LineString", "Polygon" and "Icon",
        "common": {
            "style": {
                /****** For LineString and Polygon ******/
                "color": "#FFF",
                "weight": 1,
                "opacity": 1,
                "fillColor": "#FFF",
                "fillOpacity": 1,
                "lineCap": null,
                "lineJoin": null,
                "clickable": false,
                "label": {
                    "boundPolygon": true,
                    "opacity": 0,
                    "fill": true,
                    "stroke": false,
                    "color": "#000",
                    "fillOpacity": 1,
                    "fillColor": "#454545",
                    "textAlign": "center",
                    "textBaseline": "middle",
                    "font": "13px/1.4 Helvetica",
                    "textContent": "%name%"
                },
                /****** For LineString and Polygon ******/
                
                /****** For Point and MultiPoint ******/
                "radius": 0.8,
                /****** For Point and MultiPoint ******/
                
                /****** For Icon ******/
                "rotate": 0,
                "url": "path/to/image.png",
                "size": [32, 32],
                "fixedSize": {"icon": ["1.8m", "1.8m"]}
                /****** For Icon ******/
            }
        },
        "filter": [{
            "property": "key",
            "values": {
                "val1": {
                    "fillColor": "#000"
                }，
                "val2": {
                    "fillColor": "#111"
                }
            }
        }]
    }
}
```
在这个JSON对象中，第一级的键为图层类型，值为图层样式配置。其中每个`layer_type`必须唯一。在由开放平台提供的数据中，默认包含`frame_Polygon`, `shop_Polygon`, `publicService_Polygon`和`publicService_Point`四种类型的数据，其layer_type分别对应`frame`, `shop`, `publicService`和`publicService`。**注意：**此处`publicService_Polygon`和`publicService_Point`均对应`publicService`，若您想用配置文件为这两种类型的数据配置样式，请使用`options`中的`layer_type`强制覆盖其中一种图层类型。

JSON对象的第二级支持三个键，分别为

| 键名称 | 值类型 | 描述 |
| -- | -- | -- |
| `"type"` | `<String>` | 指定地理几何数据的类型，值可以是`"inherit"`, `"Point"`, `"MultiPoint"`, `"LineString"`, `"Polygon"`或`"Icon"`中的任意一个。当设为`"inherit"`时，会读取开放平台数据中附带的类型信息。若您想强制覆盖开放平台提供的数据类型（例如将折线渲染为多边形），可以在此处强制指定。当您想要将点集渲染为Marker时，需要将此处指定为`"Icon"`。 |
| `"common"` | `<Object>` | 指定默认的渲染样式，渲染样式的格式与内容和`NGR.Path`, `NGR.Polygon`, `NGR.CanvasMarker`的`options`相同。在样式的值中被百分号括起来的变量是数据中的属性字段，在渲染时将根据实际数据解析这些字段， 可以参阅开放平台数据文档获取属性字段的列表和详细描述。 |
| `"filter"` | `<Object>` | 指定特定内容的渲染样式。`filter`是一个数组，在处理样式时，将依次在`common`样式的基础上根据特定的属性匹配覆盖一些默认样式。数组中每个元素为一个`Object`，`"property"`对应着特定属性字段的键，`"values"`对应的是值列表，对应特定属性字段的值。当该值与当前数据中的属性值匹配时，将会用特定的渲染样式覆盖默认渲染样式。可以利用这个功能完成为特定分类的店铺上色，或为不同类型的点指定不同的图标等操作。 |


## 以编程的方式配置样式
除了`styleConfig`和`layer_type`外，选项中提供的另外几个配置函数可以以编程的方式配置样式。例如：
```javascript
NGR.featureLayer(data, {
    pointToLayer: function(feature, latlng) {
        // 将所有的地理点类型定义为canvaslable，内容设置为开放平台提供数据中的name字段的值
        return NGR.canvaslabel(latlng, {textContent: feature.properties.name});
    },
    style: function(feature) {
        // 返回一个对象或将 style 直接定义为一个 Object
        return {
            // 若数据中category字段为1234，则设置背景为白色，否则设置背景为黑色
            fillColor: (feature.properties.category === 1234 ? "#FFF" : "#000")
        };
    },
    onEachFeature: function(feature, layer) {
        // 为地理图形绑定弹出窗口，内容为 "Hello" 加上数据中name字段的值
        layer.bindPopup("Hello " + feature.properties.name);
    },
    filter: function(feature, layer) {
        // 不渲染数据中category字段为5678的图形
        if (feature.properties.category === 5678) { return false; }
        return true;
    }
}).addTo(map);
```