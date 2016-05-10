# NGR.LocationProvider
`NGR.LocationProvider`可以提供室内定位服务。您可以使用它监视特定的MAC地址或查看某一楼层所有设备的位置信息。注意：一个`NGR.LocationProvider`实例最多可以同时跟踪**一层楼面**和若干个IP地址，要监控多个楼面，请使用多个`NGR.LocationProvider`实例。

## 简单用法
```javascript
var locationProvider = new NGR.LocationProvider({
          appKey: "AppKey"
        });

// 跟踪单个MAC地址
locationProvider.watch(NGR.LocationProvider.MAC, "11:22:33:44:55:66");
// 监控整个楼面上的所有设备
locationProvider.watch(NGR.LocationProvider.PLANAR_GRAPH, floorId);

// 当设备进入监控区域时触发
locationProvider.on('enter', function(feature) {
    console.log("MAC: ", feature.properties.id_data);
    console.log("Location: ", feature.geometry.coordinates);
});

// 当设备在监控区域内移动时触发
locationProvider.on('move', onMove);
// 当设备离开监控区域时触发
locationProvider.on('out', onOut);

// 开始监控
locationProvider.start();

// 终止监控
locationProvider.terminate();
```

## 选项
| 选项 | 类型 | 默认值 | 描述 |
| -- | -- | -- | -- |
| `timeout` | `Number` | `30000` | 以毫秒计的超时时间。当一个触发了`enter`事件的点在指定时间内没有发生移动行为，即告超时。超时后会触发`out`事件。 |

## 常量
下列常量可以用在`watch`和`unwatch`方法中，用作指示监控对象的类型。

| 常量 | 描述 |
| -- | -- |
| `MAC` | 监控特定的MAC地址 |
| `PLANAR_GRAPH` | 监控指定的楼层 |

## 方法
| 方法 | 返回值 | 描述 |
| -- | -- | -- |
| `watch( <Watch type> type, <String or Number> typeId)` | `this` | 监控指定设备或楼层 |
| `unwatch( <Watch type> type, <String or Number> typeId)` | `this` | 取消对指定设备或楼层的监控 |
| `start()` | `this` | 启动监控 |
| `terminate()` | `this` | 终止监控 |

## 事件
| 事件 | 数据类型 | 描述 |
| -- | -- | -- |
| `enter` | `Feature` | 当设备第一次出现在监控区域内时被触发，您可以访问`Feature`来获取详细的定位信息 |
| `move` | `Feature` | 当设备在监控区域内移动时被触发 |
| `out` | `Feature` | 当设备移出监控区域或在`timeout`时间内没有活动后被触发 |