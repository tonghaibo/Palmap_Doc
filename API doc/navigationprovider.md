# NGR.NavigationProvider
`NGR.NavigationProvider`为室内地图提供了室内静态导航支持。一个`NavigationProvider`的实例一次只能规划一条线路。

##简单用例
```javascript
var naviProvider = NGR.navigationProvider();
// 将起点和终点设置在给定楼层中给定的点上
naviProvider.setFrom(NGR.latLng(31, 121), 12345);
naviProvider.setDestination(NGR.latLng(31.5, 121.5), 12345);
// 执行导航
naviProvider.navigate().then(function() {
    // 获取原始导航数据
    console.log(naviProvider.getRawRoutines());
	//获得离最近导航线的距离和交点
	var closestPoint = naviProvider.getClosestPoint(12345, 1, 1);
    // 获取并渲染特定楼层上的导航线数据
    map.addLayer(
        NGR.featureLayer(naviProvider.getRoutinesOnPlanarGraph(12345)));
});
```

## 方法
| 方法 | 返回值 | 描述 |
| -- | -- | -- |
| `setFrom(<LatLng> latlng, <Number> planarGraphId)` | `this` | 将指定楼层上的某一点设置为导航起点 |
| `setDestination(<LatLng> latlng, <Number> planarGraphId)` | `this` | 将指定楼层上的某一点设置为导航终点 |
| `navigate()` | `Promise` | 设定起点和终点后，执行导航。此操作为异步操作，执行后将返回一个`Promise`对象，操作成功后可以通过访问`getRawRoutines`和`getRoutinesOnPlanarGraph`方法访问导航数据 |
| `getRawRoutines()` | `Object` | 获取以`GeoJSON Point`形式提供的关键导航点（包括楼层数据） |
| `getRoutinesOnPlanarGraph(<Number> planarGraphId)` | `Object` | 获取以`GeoJSON LineString`形式提供的导航线，可以将其直接作为`NGR.FeatureLayer`的数据源，直接在地图上渲染导航线 |
| `getClosestPoint(<Number> planarGraphId, <Number> x, <Number> y)` | `Object` | 通过传入的楼层id和点坐标来获取从该点到当前楼层下的导航先最短距离和最短距离的交点 |
| `getNaviLineDistance()` | `Number` | 获取导航线的长度 |