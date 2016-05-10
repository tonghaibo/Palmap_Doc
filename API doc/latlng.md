# NGR.LatLng
该类代表一个通过经纬度标识的地理坐标。

```javascript
var latlng = NGR.latLng(31, 121);
```

除了`NGR.LatLng`对象，SDK还接受普通数组和对象形式的经纬度表示，下面这些形式是等价的：
```javascript
map.panTo([31, 121]);
map.panTo({ lat: 30, lon: 121 });
map.panTo({ lon: 121, lat: 30 });
map.panTo(NGR.latLng(31, 121));
```

## 创建方法
| 创建方法 | 描述 |
| -- | -- |
| `NGR.latLng( <Number> latitude, <Number> longitude )` | 通过给定的经纬度创建一个`NGR.LatLng`对象 |

## 属性
| 属性 | 类型 | 描述 |
| -- | -- | -- |
| `lat` | `Number` | 以弧度制表示的纬度 |
| `lng` | `Number` | 以弧度制表示的经度 |

## 方法
| 方法 | 返回值 | 描述 |
| -- | -- | -- |
| `distanceTo( <LatLng> otherLatLng )` | `Number` | 返回以米为单位的与给定地理坐标的距离 |
| `equals( <LatLng> otherLatLng )` | `Boolean` | 如果两个地理坐标点在同一个地点，则返回`true` |
| `toString()` | `String` | 返回以字符串表示的经纬度坐标 |
