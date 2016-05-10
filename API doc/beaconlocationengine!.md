# NGR.BeaconLocationEngine
`NGR.BeaconLocationEngine`提供蓝牙定位的功能，封装了蓝牙定位算法。

## 方法
| 方法 | 返回值 | 描述 |
| -- | -- | -- |
| `fetchBeaconConfig( <BeaconLocationEngine options> options)` | `Promise` | 获取开放平台上的对应的点位数据库 |
| `initBeaconConfig( <Object> beaconConfig)` | `this` | 初始化点位数据库|
| `locate(<Object> beacons)` | `Object` | 通过beacon信息完成定位|