# NGR.DataSource

`NGR.DataSource`是用来查询地图数据的接口，通过该接口可以查询地图数据并交由地图引擎绘制。

## 简单用例
要渲染地图，首先需要获取地图所在的精确区域编号，通过区域查询到地图编号，再通过地图编号查询到楼层号。

地图所在的精确区域可以通过`requestRegions()`方法查询，该方法返回的Promise中将携带一个树状数据结构，树的叶子节点中的`code`字段即为精确区域编号。除了使用API查询以外，也可以向销售代表索要行政区划列表来获取对应ID。

在获取到精确区域编号以后，就可以通过`requestMaps`方法查询对应的地图信息和楼层编号，以上海图聚信息技术有限公司为例：

```
var datasource = new NGR.DataSource({
  AppKey: 'xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx'
});

datasource.requestMaps({region_code: '310113'})     //此处310113为宝山区编号
.then(function(maps) {
    for(var i = 0; i < maps.list.length; ++i) {
        if (maps.list[i].name === "文渊楼") {
            return maps.list[i].id;
        }
    }
}).then(function(map_id) {
    return datasource.requestFloors(map_id)
    .then(function(floors) {
        console.log(floors.list);   // 此处可以缓存查询到的楼层供切换使用
        return floors.list[0].id;   // 此处返回您需要的楼层
    });
}).then(function(planar_graph_id) {
    ...     // 通过requestPlanarGraph请求楼层数据并进行渲染
});
```

## 创建方法
| 方法 | 描述 |
| -- | -- |
| `new NGR.DataSource(options)` | 返回一个DataSource实例 |

## 选项
| 选项 | 类型 | 默认值 | 描述 |
| -- | -- | -- | -- |
| `AppKey` | `String` | `null` | 由开放平台分配的AppKey |


## 方法
| 方法 | 返回值 | 描述 |
| -- | -- | -- |
| `requestRegions()` | `Promise` | 查询行政区划。正常回调的Promise将携带一个树状数据结构，每个节点的结构为：`{"type": "str", "code": "str", "name": "str", "children": 指向另一个节点}`|
    | `requestCategories( <String> type, <Number> id )` | `Promise` | 查询所在区域内所有可用的分类。`type` 目前只能为`"region"`，`id`必须是数字，可以通过`requestRegions()`方法查询到，并且只能使用查询到的叶子节点的`id`。正常回调的Promise将携带一个数组，每个元素的结构为：`{"category": "str", "id": 1234}` |
| `requestMaps( <Object> filter )` | `Promise` | 查询地图信息。`filter`是一个形如 `{region_code: 0123, category_id: 4567, "start": 0}`的对象，其中`region_code`可以通过`requestRegions()`方法查询到，并且只能使用查询到的叶子节点的`region_code`，`category_id`可以通过`requestCategories()`方法查询到，`start`是起始偏移，用于大量数据的分页。除`start`可选外，其余参数必须全部提供。正常回调的Promise将携带一个数组，每个元素都包含了单张地图的详细信息 |
| `requestFloors( <Number> map_id )` | `Promise` | 查询某个map的楼层信息。正常回调的Promise将携带一个对象，其中的`list`键对应一个数组，数组中的每个元素对应一个楼层 |
| `requestPlanarGraph( <Number> floorId )` | `Promise` | 查询楼层编号为`floorId`的楼层信息。正常回调将返回对应的楼层信息，参照快速入门可以使用渲染引擎渲染这些信息 |
| `requestShops( <String or Number> floorId, <Number> start? )` | `Promise` | 请求特定楼层中所有的商铺，接口返回的是分页后的结果，可以通过`start`指定起始的页数 |
| `requestPOIDetail( <String or Number> poiId )` | `Promise` | 请求编号为`poiId`的POI的详细信息 |
| `POISearch( <Object> filter )` | `Promise` | 根据`filter`搜索POI的基本信息，`filter`可以包含下列字段：`<String> word`为POI关键字，`Array<String> map_id_list`为要搜索的地图的范围，`Array<String> building_id_list`为要搜索的建筑物的范围，`Array<String> floor_id_list`为要搜索的楼层的范围，`Array<String> category_id_list`为要搜索的分类的范围。另外可以在`filter`中指定分页的起始页数`start` |
