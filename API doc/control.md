# NGR.Control
所有SDK控件的基类。实现了`IControl`接口，您可以通过如下方法向地图中添加控件：
```javascript
control.addTo(map);
// 或是
map.addControl(control);
```

## 创建方法
| 创建方法 | 描述 |
| -- | -- |
| `NGR.Control( <Control options> options? )` | 通过给定选项创建一个控件 |

## 选项
| 选项 | 类型 | 默认值 | 描述 |
| -- | -- | -- | -- |
| `position` | `String` | `topright` | 控件的初始位置（地图四个角中的一个） |

## 方法
| 方法 | 返回值 | 描述 |
| -- | -- | -- |
| `setPosition( <String> position )` | `this` | 为控件设置位置 |
| `getPosition()` | `String` | 返回控件的位置 |
| `addTo( <Map> map )` | `this` | 将控件添加到地图中去 |
| `removeFrom( <Map> map )` | `this` | 从地图中移除控件 |
| `getContainer()` | `HTMLElement` | 获取控件的HTML容器 |

## 控件位置
控件（在地图角落的）位置以字符串形式表示。与地图边缘的边距是通过CSS设定的。

| 位置 | 描述 |
| -- | -- |
| `topleft` | 地图的左上角 |
| `topright` | 地图的右上角 |
| `bottomleft` | 地图的左下角 |
| `bottomright` | 地图的右下角 |
