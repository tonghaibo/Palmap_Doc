# NGR.LatLngBounds
`NGR.LatLngBounds`代表在地图上的一个矩形的地理区域。

## 简单用例
```javascript
var southWest = NGR.latLng(31, 121),
    northEast = NGR.latLng(32, 122),
    bounds = NGR.latLngBounds(southWest, northEast);
```
主要的SDK方法均支持通过数组表示地理区域的方法，下面的调用方法也是合法的：
```javascript
map.fitBounds([
    [31, 121],
    [32, 122]
]);
```
## 创建方法
| 创建方法 | 描述 |
| -- | -- |
| `NGR.latLngBounds( <LatLng> southWest, <LatLng> northEast )` | 通过给定的西南角和东北角的坐标，创建一个矩形的地理区域 |
| `NGR.latLngBounds( <LatLng[]> latlngs )` | 创建一个能够包含所有给出点的矩形地理区域 |

# 方法
| 方法 | 返回值 | 描述 |
| -- | -- | -- |
| `extend( <LatLng or LatLngBounds> latlng )` | `this` | 扩展区域直至使其能够包含给定的坐标或区域 |
| `getSouthWest()` | `NGR.LatLng` | 返回区域的西南点坐标 |
| `getNorthEast()` | `NGR.LatLng` | 返回区域的东北点坐标 |
| `getNorthWest()` | `NGR.LatLng` | 返回区域的西北点坐标 |
| `getSouthEast()` | `NGR.LatLng` | 返回区域的东南点坐标 |
| `getWest()` | `Number` | 返回区域最西侧的经度值 |
| `getSouth()` | `Number` | 返回区域最南侧的纬度值 |
| `getEast()` | `Number` | 返回区域最东侧的经度值 |
| `getNorth()` | `Number` | 返回区域最北侧的纬度值 |
| `getCenter()` | `NGR.LatLng` | 返回区域的中心点 |
| `contains( <LatLngBounds> otherBounds )` | `Boolean` | 判断区域中是否包含给定的区域 |
| `contains( <LatLng> latlng )` | `Boolean` | 判断区域中是否包含给定的点 |
| `intersects( <LatLngBounds> otherBounds )` | `Boolean` | 判断区域是否与给定的区域相交 |
| `equals( <LatLngBounds> otherBounds )` | `Boolean` | 判断区域与给定的区域是否相同 |
| `pad( <Number> bufferRatio )` | `NGR.LatLngBounds` | 返回一个依据扩展比扩展后的区域。 |
| `isValid()` | `Boolean` | 指示区域是否已经被正确初始化 |

